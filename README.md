# Run a K2 Validator

## Table of Contents

## Validator Requirements

### Minimum Koii requirements

There is no minimum amount of KOII required to stake and participate in the voting process.

To participate in the voting process you must configure your system, start a validator, and configure your voting and stake accounts. This guide will show you how to do this.

### Hardware requirements

Here are the minimum hardware requirements for running a K2 Validator in terms of memory, computing, storage, and your operating system:

- Memory
    - 256GB, or more for consensus validator nodes
    - 512GB, or more for RPC nodes
- Compute
    - 12 cores / 24 threads, or more @ minimum of 2.8GHz for consensus validator nodes
    - 16 cores / 32 threads, or more for RPC nodes
- Storage
    
    <aside>
    💡 Accounts and ledger *can* be stored on the same disk, however due to high IOPS, this is not recommended
    
    </aside>
    
    For consensus validators:
    
    - PCIe Gen3 x4 NVME SSD, or better
    - Accounts: 500GB, or larger. High TBW (Total Bytes Written)
    - Ledger: 2TB or larger. High TBW suggested
    
    For RPC nodes:
    
    - A larger ledger disk if longer transaction history is required, accounts and ledger should not be stored on the same disk
    - GPUs are not strictly necessary
    - Network: 1 Gbps uplink and downlink speed, must be unshaped and unmetered
    - Operating System

Currently, we are testing our binaries for Ubuntu 22.04. We do provide binaries for other operating systems however the operation of these binaries is not guaranteed.

Once a properly sized Ubuntu 22.04 system is available we can begin to configure the system for operation of a validator node.

---

## Pre-requisites setup

> **All following steps need to be run on the validator server, unless mentioned otherwise.**
> 

### 1. Ensure system is up-to-date

Ensure your Ubuntu system is up-to-date and has all the base packages required

```bash
sudo apt update && sudo apt upgrade
sudo apt install libssl-dev libudev-dev pkg-config zlib1g-dev llvm clang
```

### 2. User setup

```bash
sudo adduser koii
sudo usermod -aG sudo koii
sudo su koii
cd ~
```

<aside>
⚠️ Please ensure that all the **following steps** happen within the home directory (/home/koii) of the `koii` user

</aside>

### 3. Koii cli setup

* Required both on your secure computer for keypair generation and on the validator

```bash
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init_v1.16.6.sh)"
# You may need to update PATH variable for the cli to be available
echo 'export PATH="/home/koii/.local/share/koii/install/active_release/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
# Set the koii config to point to the testnet
koii config set --url https://mainnet.koii.network

```

### 4. Key pairs creation

> Run commands for **only this step** on a **secure computer** **separate from the validator server**
You need to **install Koii cli on this secure computer** as well, to be able to use the  commands below
> 

We will be creating the following 4 key pairs:

```bash
koii-keygen new --outfile ~/validator-keypair.json
koii-keygen new --outfile ~/vote-account-keypair.json
koii-keygen new --outfile ~/stake-account-keypair.json
koii-keygen new --outfile ~/authorized-withdrawer-keypair.json
# To print your Public key(i.e. Wallet address) for any keypairs
# koii-keygen pubkey <Path to Keypair>
```

- **validator-keypair.json :** Identity of the validator on the network
    - Copy this to the remote validator server at `/home/koii/validator-keypair.json`
- **vote-account-keypair.json** : Voting account on the network
    - Copy this to the remote validator server at `/home/koii/vote-account-keypair.json`
- **stake-account-keypair.json** : Keypair for your staking wallet
    - Keep this secure since this will hold the wallet that you delegate stake from
- **authorized-withdrawer-keypair.json** : Authorized withdrawer keypair, allowd to withdraw funds from your validator vote account ****

<aside>
⚠️ The **authorized withdrawer keypair** is the ultimate authority over your validator. This keypair will be able to withdraw from your vote account and will have additional permission to change all other aspects of your vote account.
*Anyone in possession of it can permanently take control of your vote account and make any changes as they please.*

</aside>

<aside>
💡 **`stake-account-keypair.json`**  and **`authorized-withdrawer-keypair.json`** must be stored in a secure location **NOT on the validator.**

</aside>

### 5. Network configuration

If you have firewall software installed you will need to allow traffic on the following ports:

```bash
sudo ufw allow 10000:10500/udp
sudo ufw allow 10000:10500/tcp
sudo ufw allow 10899/tcp
sudo ufw allow 10900/tcp
```

### 6. Systuning setup

- Create a file at `/etc/systemd/system/systuner.service` :
    
    ```bash
    [Unit]
    Description=Koii System Tuner 
    After=network.target 
    [Service]
    Type=simple 
    Restart=on-failure 
    RestartSec=1 
    ExecStart=/home/koii/.local/share/koii/install/active_release/bin/koii-sys-tuner --user koii
    [Install]
    WantedBy=multi-user.target
    
    ```
    
- Start and Enable the service to automatically start
    
    ```bash
    sudo systemctl start systuner
    sudo systemctl enable systuner
    ```
    

---

## Validator setup

### 1. Systemd service setup

**Copy the following file to `/home/koii/validator.sh` and make it executable**

```bash
#!/bin/sh
exec /home/koii/.local/share/koii/install/active_release/bin/koii-validator \
    --identity /home/koii/validator-keypair.json  \
    --vote-account /home/koii/vote-account-keypair.json \
    --ledger /home/koii/ledger/ledgerdb \
    --accounts /home/koii/accounts/accountdb \
    --log /home/koii/koii-rpc.log \
    --rpc-bind-address 0.0.0.0 \
    --rpc-port 10899 \
    --gossip-port 10001 \
    --dynamic-port-range 10002-10500 \
    --enable-rpc-transaction-history \
    --known-validator BPRAynHogErzYmEtAaeJFugRozXuU6EEqNa4rEKtF4mS \
    --known-validator GqmBXoaetkMXzrMhCijJDsL5J4KDvDFzZuMEpoXYUowc \
    --known-validator Hajii3WYcyRWDzENPJwaY2WGtNpYQ7vrCqpgaUi8fsUo \
    --known-validator Fme35immspxuG6fboueneNDque5xLu62Ca2BHRuLgTSV \
    --entrypoint entrypoint-1.mainnet.koii.network:10001 \
    --entrypoint entrypoint-2.mainnet.koii.network:10001 \
    --entrypoint entrypoint.mainnet.haji.ro:10001 \
    --entrypoint entrypoint-koii-mainnet.stakecraft.com:10001 \
    --rpc-faucet-address rpc-faucet.testnet.koii.network:9900 \
    --init-complete-file /home/koii/init-completed \
    --no-wait-for-vote-to-start-leader \
    --enable-extended-tx-metadata-storage \
    --maximum-full-snapshots-to-retain 20 \
    --maximum-incremental-snapshots-to-retain 20 \
    --limit-ledger-size 200000000 \
    --only-known-rpc \
    --wal-recovery-mode skip_any_corrupted_record \
    --expected-genesis-hash 7rVVciNgm2m5JquMbKNxEYPryvzVtDktWhHLM4xFpfjq

```

**Create a systemd unit file at `/etc/systemd/system/koii-validator.service`** 

```bash
[Unit]
Description=Koii Validator 
After=network.target 
Wants=systuner.service 
StartLimitIntervalSec=0 
[Service]
User=koii
Group=koii
LimitNOFILE=1000000
LogRateLimitIntervalSec=0
Environment="PATH=/home/koii/.local/share/koii/install/active_release/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
ExecStart=/home/koii/validator.sh
Restart=on-failure
RestartSec=10
[Install]
WantedBy=multi-user.target
```

### 2. Create a vote account

<aside>
🚧 You will need your validator keypair account to be funded with KOII tokens before continuing

</aside>

<aside>
⚠️ Please make sure your Koii CLI is configured for `mainnet.koii.network` and using your validator identity before continuing:

`koii config set --url [https://mainnet.koii.network](https://testnet.koii.network/) --keypair ~/validator-keypair.json`

</aside>

Run the following command to create a vote-account on the network:

```bash
koii create-vote-account ~/vote-account-keypair.json ~/validator-keypair.json ~/authorized-withdrawer-keypair.json
```

### 3. Enable and Start the Koii validator

```bash
sudo systemctl enable koii-validator.service
sudo systemctl start koii-validator.service
sudo systemctl status koii-validator.service
```

### 4. Configure the Commission Rate for Your Validator

The commission rate determines the percentage of staking rewards allocated to the validator as a fee for their services, with the remainder distributed to the stakers. The commission rate must be a valid percentage between 0 and 100.

To update the commission rate for your validator's vote account, use the following command:

```bash
koii vote-update-commission <VOTE_ACCOUNT_ADDRESS> <NEW_COMMISSION> --authorized-voter <PATH_TO_AUTHORIZED_VOTER_KEYPAIR>
```
### 5. Update Your Validator Information

To update or publish your validator's information on the Koii network, use the following command:

```bash
koii validator-info publish "<VALIDATOR_NAME>" -w "<WEBSITE_URL>"
```
---

## Staking KOII in the validator

> Commands in this section are to be run on the computer which has the stake account key pair (**NOT ON VALIDATOR**)

### 1. Create a stake account

Run the following command, AFTER replacing <AMOUNT_TO_STAKE>.

```bash
koii create-stake-account ~/stake-account-keypair.json <AMOUNT_TO_STAKE> --stake-authority ~/validator-keypair.json --withdraw-authority ~/authorized-withdrawer-keypair.json
```

### 2. Delegate the stake to your validator

```bash
koii delegate-stake ~/stake-account-keypair.json ~/vote-account-keypair.json --stake-authority ~/validator-keypair.json --force
```

### 3. Check your delegated stake’s status

Your validator will not show up in the koii validators list for 12 to 24 hours, you can check your stake to make sure it is properly delegated by running the following command

```bash
koii stake-account ~/stake-account-keypair.json
```

Expected output:

```bash
Balance: <Amount of KOII>
Rent Exempt Reserve: <Amount of KOII>
Delegated Stake: <Amount of KOII>
Activating Stake: <Amount of KOII>
Delegated Vote Account Address: <pubkey>
Stake Authority: <pubkey>
Withdraw Authority: <pubkey>
```

If you see a value in “Activating Stake” then you should be successfully voting within 24 hours
