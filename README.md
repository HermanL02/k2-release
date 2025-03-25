# K2 Network: High-Performance Blockchain Infrastructure

## 🌐 Project Overview

K2 is a cutting-edge blockchain network developed by Koii Network, designed to revolutionize decentralized computing through high-performance, scalable, and efficient blockchain infrastructure. This repository contains installation scripts and initialization tools for setting up K2 network nodes.

### Purpose
- Provide a robust, high-throughput blockchain platform
- Enable decentralized computing with advanced network infrastructure
- Support validators and node operators in deploying K2 network components

## 🚀 Features / Capabilities

- High-throughput blockchain architecture
- Secure proof-of-stake consensus mechanism
- Dynamic validator configuration
- Cross-chain interoperability
- Modular and flexible network design
- Multi-version installation support

## 🔧 Technologies Used

- **Primary Language**: Rust
- **Blockchain Platform**: Koii Network K2
- **Consensus Mechanism**: Proof-of-Stake (PoS)
- **Installation Scripts**: Bash/Shell
- **Supported Operating System**: Ubuntu 22.04 LTS

## 💻 System Requirements

### Hardware Specifications
| Node Type | Memory | Compute | Storage |
|-----------|--------|---------|---------| 
| Consensus Node | 256GB | 12 cores / 24 threads @ 2.8GHz | 500GB PCIe NVME SSD |
| RPC Node | 512GB | 16 cores / 32 threads | 2TB High TBW NVME SSD |

### Network Configuration
- **Firewall Ports**: 
  - 10000-10500 (UDP/TCP)
  - 10899/TCP
  - 10900/TCP
- **Network Connection**: 1 Gbps symmetric

## 🗂️ Project Structure

### Installation Scripts
| Script | Version | Purpose |
|--------|---------|---------|
| `k2-install-init.sh` | Latest | Primary installation initialization script |
| `k2-install-init_v*.sh` | v1.14.19 - v1.16.6 | Version-specific installation scripts |

## 🚀 Getting Started

### Prerequisites
- Ubuntu 22.04 server
- Sudo access
- Basic networking knowledge
- KOII tokens for staking

### Installation Steps
```bash
# Update system packages
sudo apt update && sudo apt upgrade

# Install dependencies
sudo apt install libssl-dev libudev-dev pkg-config zlib1g-dev llvm clang

# Create Koii user
sudo adduser koii
sudo usermod -aG sudo koii

# Install Koii CLI
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init_v1.16.6.sh)"
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a pull request

### Contribution Guidelines
- Follow existing code structure
- Ensure compatibility with latest K2 network version
- Include comprehensive testing

## 📜 License

Refer to the Koii Network official licensing terms.

## 🔗 Additional Resources

- [Koii Network Official Website](https://koii.network)
- [K2 Network Documentation](https://docs.koii.network)
- [Community Support Channel](https://discord.gg/koii)

## 📞 Support

For technical support, community assistance, or reporting issues:
- Open a GitHub Issue
- Join the Koii Network Discord
- Email: support@koii.network