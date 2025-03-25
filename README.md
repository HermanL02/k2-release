# K2 Network: Decentralized Blockchain Infrastructure Installation Scripts

## 🌐 Project Overview

K2 is an advanced blockchain network developed by Koii Network, designed to provide a high-performance, scalable, and efficient decentralized computing infrastructure. This repository contains installation initialization scripts for setting up K2 network nodes across multiple versions.

### Purpose
- Provide automated installation scripts for K2 network nodes
- Support multiple Ubuntu server configurations
- Enable easy deployment of blockchain infrastructure

## 🚀 Features

- Version-specific installation scripts (v1.14.19 - v1.16.6)
- Comprehensive system and network compatibility checks
- Automated dependency management
- Flexible installation options
- Support for consensus and RPC node configurations

## 🔧 Installation Scripts

### Available Versions
- `k2-install-init_v1.14.19.sh`: Early release
- `k2-install-init_v1.14.20.sh`: Minor improvements
- `k2-install-init_v1.14.21.sh`: Network stability updates
- `k2-install-init_v1.16.0.sh`: Major feature release
- `k2-install-init_v1.16.6.sh`: Latest stable version

## 💻 System Requirements

### Minimum Hardware Specifications
| Node Type | Memory | Compute | Storage |
|-----------|--------|---------|---------| 
| Consensus Node | 256GB | 12 cores / 24 threads @ 2.8GHz | 500GB PCIe NVME SSD |
| RPC Node | 512GB | 16 cores / 32 threads | 2TB High TBW NVME SSD |

### Software Prerequisites
- Ubuntu 22.04 LTS Server
- Sudo access
- Basic networking knowledge
- KOII tokens for staking

## 🚀 Quick Start Guide

### Installation Steps
```bash
# Update system packages
sudo apt update && sudo apt upgrade

# Install dependencies
sudo apt install libssl-dev libudev-dev pkg-config zlib1g-dev llvm clang

# Create Koii user
sudo adduser koii
sudo usermod -aG sudo koii

# Install Koii CLI (Latest Version)
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init_v1.16.6.sh)"
```

## 🔧 Technologies Used
- **Blockchain Platform**: Koii Network K2
- **Consensus Mechanism**: Proof-of-Stake (PoS)
- **Primary Language**: Rust
- **Installation Scripts**: Bash/Shell
- **Target OS**: Ubuntu 22.04 LTS

## 🤝 Contributing
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a pull request

### Contribution Guidelines
- Follow existing code structure
- Ensure compatibility with the latest K2 network version
- Include comprehensive testing

## 📞 Support
- Open a GitHub Issue
- Join the [Koii Network Discord](https://discord.gg/koii)
- Email: support@koii.network

## 🔗 Additional Resources
- [Koii Network Official Website](https://koii.network)
- [K2 Network Documentation](https://docs.koii.network)

## 📜 License
Refer to the Koii Network official licensing terms.

---

**Note**: Always refer to the latest official documentation for the most up-to-date installation instructions and network requirements.