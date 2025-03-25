# K2 Network Validator Installation and Setup Guide

## 🌐 Project Overview

K2 is a high-performance blockchain network developed by the Koii Network, designed to provide a scalable and efficient blockchain infrastructure. This repository contains comprehensive resources for setting up and running a K2 validator node.

### Key Features
- Detailed validator setup instructions
- Multiple installation scripts for different versions
- Comprehensive network configuration guidelines
- Staking and validator management documentation

## 🗂️ Repository Structure

### Directories
- **/**: Root directory containing installation and setup scripts
  - `k2-install-init.sh`: Primary installation initialization script
  - `k2-install-init_v*.sh`: Version-specific installation scripts

### Key Files
- `k2-install-init_v1.16.6.sh`: Latest version installation script
- `README.md`: Main documentation and setup guide
- Validator configuration and system setup scripts

## 🔧 Technical Details

### Technologies Used
- **Blockchain**: Koii Network K2 blockchain
- **Installation**: Shell scripting
- **Operating System**: Ubuntu 22.04 (primary support)
- **Languages**: Bash, Shell scripting

### Architecture Overview
- Decentralized validator network
- Proof-of-stake consensus mechanism
- Dynamic validator configuration
- Modular installation process

### Validator Requirements

#### Minimum Hardware
- **Memory**: 
  - 256GB for consensus nodes
  - 512GB for RPC nodes
- **Compute**: 
  - 12 cores / 24 threads @ 2.8GHz (consensus)
  - 16 cores / 32 threads (RPC)
- **Storage**:
  - PCIe Gen3 x4 NVME SSD
  - Accounts: 500GB, high TBW
  - Ledger: 2TB, high TBW suggested

#### Network Configuration
- Firewall ports: 10000-10500 (UDP/TCP)
- 10899/TCP and 10900/TCP
- 1 Gbps symmetric network connection

## 🚀 Quick Start

### Prerequisites
1. Ubuntu 22.04 server
2. Sudo access
3. Basic networking knowledge
4. KOII tokens for staking

### Installation Steps
```bash
# Update system
sudo apt update && sudo apt upgrade

# Install dependencies
sudo apt install libssl-dev libudev-dev pkg-config zlib1g-dev llvm clang

# Create Koii user
sudo adduser koii
sudo usermod -aG sudo koii

# Install Koii CLI
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init_v1.16.6.sh)"
```

## 📖 Full Documentation
For comprehensive setup instructions, refer to the existing README sections:
- Validator Requirements
- Pre-requisites Setup
- Validator Setup
- Staking KOII in the Validator

## 🤝 Contributing
- Follow existing setup guidelines
- Ensure compatibility with latest K2 network version
- Test thoroughly before submitting changes

## 📜 License
Refer to the original Koii Network licensing terms.

## 🔗 Resources
- [Koii Network Official Website](https://koii.network)
- [K2 Network Documentation](https://docs.koii.network)

## 📞 Support
For support, join the Koii Network community channels or open an issue in this repository.