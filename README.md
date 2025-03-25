# K2 Network: High-Performance Blockchain Infrastructure Installation Scripts

## 🌐 Project Overview

K2 is an advanced blockchain network developed by Koii Network, designed to provide a high-performance, scalable, and efficient decentralized computing infrastructure. This repository contains installation scripts and initialization utilities for setting up K2 network nodes.

### Key Objectives
- Simplify K2 network node deployment
- Provide version-specific installation scripts
- Support seamless blockchain infrastructure setup

## 🚀 Features and Capabilities

### Installation Script Highlights
- Multi-version support (v1.14.19 - v1.16.6)
- Cross-platform compatibility (Linux, macOS)
- Automated dependency management
- Flexible configuration options

### Supported Architectures
- x86_64 Linux (Ubuntu 22.04 LTS recommended)
- Apple Darwin (Intel and ARM64)

## 🔧 Getting Started

### Prerequisites
- Ubuntu 22.04 server (recommended)
- Sudo access
- Basic networking knowledge
- Internet connection

### Installation Steps
```bash
# Update system packages
sudo apt update && sudo apt upgrade

# Install dependencies
sudo apt install libssl-dev libudev-dev pkg-config zlib1g-dev llvm clang

# Create Koii user (optional but recommended)
sudo adduser koii
sudo usermod -aG sudo koii

# Install K2 Network Node
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init_v1.16.6.sh)"
```

## 📂 Project Structure

### Installation Scripts
| Script Name | Version | Purpose |
|------------|---------|---------|
| `k2-install-init.sh` | Latest | Primary installation script |
| `k2-install-init_v*.sh` | v1.14.19 - v1.16.6 | Version-specific installation scripts |

## 💻 System Requirements

### Minimum Hardware Specifications
| Node Type | Memory | Compute | Storage |
|-----------|--------|---------|---------|
| Consensus Node | 256GB | 12 cores / 24 threads | 500GB PCIe NVME SSD |
| RPC Node | 512GB | 16 cores / 32 threads | 2TB High TBW NVME SSD |

### Network Configuration
- Firewall Ports: 
  - 10000-10500 (UDP/TCP)
  - 10899/TCP
  - 10900/TCP
- Recommended Network Connection: 1 Gbps symmetric

## 🔧 Technologies Used
- **Blockchain Platform**: Koii Network K2
- **Consensus Mechanism**: Proof-of-Stake (PoS)
- **Primary Language**: Rust
- **Installation Scripts**: Bash/Shell

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
This project follows the Koii Network licensing terms. Please refer to the official licensing documentation.

## 🔗 Additional Resources
- [Koii Network Official Website](https://koii.network)
- [K2 Network Documentation](https://docs.koii.network)
- [Community Support Channel](https://discord.gg/koii)

## 📞 Support
For technical support:
- Open a GitHub Issue
- Join the Koii Network Discord
- Email: support@koii.network