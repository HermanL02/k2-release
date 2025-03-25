# K2 Network: High-Performance Blockchain Infrastructure Installation Scripts

## 🌐 Project Overview

K2 is a cutting-edge blockchain network developed by Koii Network, designed to provide a high-performance, scalable, and efficient decentralized computing infrastructure. This repository contains installation initialization scripts for setting up K2 network nodes across different versions.

### Purpose
The primary goal of these scripts is to simplify the deployment and initialization of K2 network nodes, supporting blockchain validators, RPC nodes, and network participants.

## 🚀 Features

- **Automated Installation**: One-click setup for K2 network nodes
- **Version Compatibility**: Multiple installation scripts supporting versions from v1.14.19 to v1.16.6
- **Cross-Platform Support**: Compatible with Linux environments (Ubuntu 22.04 LTS recommended)
- **Flexible Configuration**: Supports custom data directories and network configurations

## 🔧 Installation Scripts

### Available Versions
| Version    | Script Name                     | Status      |
|------------|--------------------------------|-------------|
| Latest     | `k2-install-init.sh`           | Recommended |
| v1.16.6    | `k2-install-init_v1.16.6.sh`   | Stable      |
| v1.16.5    | `k2-install-init_v1.16.5.sh`   | Stable      |
| v1.16.4    | `k2-install-init_v1.16.4.sh`   | Stable      |
| v1.16.3    | `k2-install-init_v1.16.3.sh`   | Stable      |
| v1.16.2    | `k2-install-init_v1.16.2.sh`   | Stable      |
| v1.16.1    | `k2-install-init_v1.16.1.sh`   | Stable      |
| v1.16.0    | `k2-install-init_v1.16.0.sh`   | Stable      |
| v1.14.21   | `k2-install-init_v1.14.21.sh`  | Legacy      |
| v1.14.20   | `k2-install-init_v1.14.20.sh`  | Legacy      |
| v1.14.19   | `k2-install-init_v1.14.19.sh`  | Legacy      |

## 💻 System Requirements

### Recommended Hardware
| Node Type      | CPU                      | RAM   | Storage                  | Network      |
|---------------|--------------------------|-------|--------------------------|--------------|
| Consensus Node| 12 cores / 24 threads    | 256GB | 500GB PCIe NVME SSD      | 1 Gbps       |
| RPC Node      | 16 cores / 32 threads    | 512GB | 2TB High TBW NVME SSD    | 1 Gbps       |

### Prerequisites
- Ubuntu 22.04 LTS
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

# Install Koii CLI (using latest version)
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init_v1.16.6.sh)"
```

## 🔧 Configuration Options

The installation script supports several configuration flags:
- `--data-dir`: Specify custom installation directory
- `--url`: Set custom JSON RPC URL
- `--pubkey`: Provide public key for update manifest
- `--no-modify-path`: Prevent modifying system PATH

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
For technical support:
- Open a GitHub Issue
- Join the Koii Network Discord
- Email: support@koii.network