# K2 Network: High-Performance Blockchain Infrastructure Installer

## 🌐 Project Overview

K2 is a cutting-edge blockchain network developed by Koii Network, designed to provide high-performance, scalable, and efficient decentralized computing infrastructure. This repository contains installation scripts and initialization tools for setting up K2 nodes and participating in the network.

## 🚀 Key Features

- 📦 Multiple version-specific installation scripts
- 🔒 Secure and modular blockchain infrastructure setup
- 🌈 Cross-platform support (Linux, macOS)
- 🔧 Flexible node configuration
- 📊 Easy network participation

## 🛠 Getting Started

### Prerequisites

- Ubuntu 22.04 LTS (recommended)
- Sudo access
- Basic networking knowledge
- KOII tokens for potential staking

### Installation Steps

```bash
# Update system packages
sudo apt update && sudo apt upgrade

# Install dependencies
sudo apt install libssl-dev libudev-dev pkg-config zlib1g-dev llvm clang

# Create Koii user (optional but recommended)
sudo adduser koii
sudo usermod -aG sudo koii

# Install K2 Network
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init_v1.16.6.sh)"
```

## 📂 Project Structure

| Script | Version | Purpose |
|--------|---------|---------|
| `k2-install-init.sh` | Latest | Primary installation script |
| `k2-install-init_v1.14.19.sh` | v1.14.19 | Early release installer |
| `k2-install-init_v1.16.6.sh` | v1.16.6 | Latest stable version installer |

## 💻 System Requirements

### Hardware Specifications
| Node Type | Memory | Compute | Storage |
|-----------|--------|---------|---------|
| Consensus Node | 256GB | 12 cores / 24 threads @ 2.8GHz | 500GB PCIe NVME SSD |
| RPC Node | 512GB | 16 cores / 32 threads | 2TB High TBW NVME SSD |

### Network Configuration
- Firewall Ports: 
  - 10000-10500 (UDP/TCP)
  - 10899/TCP
  - 10900/TCP
- Network Connection: 1 Gbps symmetric

## 🔧 Technologies Used

- **Blockchain Platform**: Koii Network K2
- **Consensus Mechanism**: Proof-of-Stake (PoS)
- **Primary Language**: Rust
- **Installation Scripts**: Bash/Shell
- **Supported OS**: Linux, macOS

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