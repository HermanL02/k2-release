# K2 Network Installation Scripts

## 🌐 Project Overview

### Purpose
K2 is an advanced blockchain network developed by Koii Network, designed to provide high-performance, scalable, and efficient decentralized computing infrastructure. This repository contains installation initialization scripts for setting up K2 network nodes.

### Key Features
- 🚀 Streamlined blockchain node deployment
- 🔒 Secure installation process
- 📊 Version-specific installation support
- 🌈 Cross-platform compatibility
- 🔧 Flexible network configuration

## 🗂️ Repository Structure

### Installation Scripts
| Script | Version | Purpose |
|--------|---------|---------|
| `k2-install-init.sh` | Latest (v1.16.2) | Primary installation initialization script |
| `k2-install-init_v*.sh` | v1.14.19 - v1.16.6 | Version-specific installation variants |

## 🔧 Technical Details

### Technologies
- **Platform**: Koii Network K2
- **Deployment**: Bash/Shell Scripts
- **Supported Architectures**: 
  - Linux (x86_64)
  - MacOS (Intel/Apple Silicon)

### Compatibility
- **Recommended OS**: Ubuntu 22.04 LTS
- **Supported Architectures**: 
  - x86_64
  - ARM64/aarch64

## 🚀 Quick Start Guide

### Prerequisites
- Ubuntu 22.04 server
- Sudo access
- Internet connectivity
- Basic server management skills

### Installation Steps
```bash
# Update system packages
sudo apt update && sudo apt upgrade

# Install dependencies
sudo apt install libssl-dev libudev-dev pkg-config zlib1g-dev llvm clang

# Create Koii user (optional but recommended)
sudo adduser koii
sudo usermod -aG sudo koii

# Run installation script
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init_v1.16.6.sh)"
```

## 💻 System Requirements

### Recommended Hardware
| Node Type | Memory | CPU | Storage |
|-----------|--------|-----|---------|
| Consensus Node | 256GB | 12 cores / 24 threads @ 2.8GHz | 500GB PCIe NVME SSD |
| RPC Node | 512GB | 16 cores / 32 threads | 2TB High TBW NVME SSD |

### Network Configuration
- **Required Firewall Ports**: 
  - 10000-10500 (UDP/TCP)
  - 10899/TCP
  - 10900/TCP
- **Recommended Network**: 1 Gbps symmetric connection

## 🤝 Contributing
1. Fork the repository
2. Create a feature branch
3. Implement changes
4. Submit a pull request

### Contribution Guidelines
- Follow existing script structure
- Test compatibility with latest K2 network version
- Include clear documentation for changes

## 📜 License
Distributed under Koii Network's official licensing terms. 

## 🔗 Resources
- [Koii Network Website](https://koii.network)
- [K2 Network Documentation](https://docs.koii.network)
- [Community Support](https://discord.gg/koii)

## 📞 Support
- Open GitHub Issues
- Join Koii Network Discord
- Email: support@koii.network

**Note**: Always refer to the latest official documentation for the most up-to-date installation instructions.