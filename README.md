# K2 Network: High-Performance Blockchain Infrastructure Installation Scripts

## 🌐 Project Overview

K2 is a cutting-edge blockchain network developed by Koii Network, providing high-performance, scalable, and efficient blockchain infrastructure. This repository contains the official installation scripts for setting up K2 nodes and initializing the network.

## 🚀 Features / Capabilities

- 📦 Multiple version-specific installation scripts
- 🔧 Flexible deployment for different system configurations
- 🌐 Cross-platform support (Linux, MacOS)
- 🔒 Secure network initialization process

## 📦 Project Structure

```
.
├── k2-install-init.sh             # Latest primary installation script
├── k2-install-init_v*.sh          # Version-specific installation scripts
└── README.md                      # Project documentation
```

## 🛠️ Technologies Used

- **Primary Language**: Shell Script (Bash)
- **Target Platform**: Linux, MacOS
- **Supported Architectures**: x86_64, ARM64
- **Operating Systems**: Ubuntu 22.04 LTS, MacOS

## 🚀 Getting Started

### Prerequisites

- Linux (Ubuntu 22.04) or MacOS
- Sudo/root access
- Internet connection
- Minimum system requirements:
  - 8GB RAM
  - 100GB Storage
  - Stable network connection

### Installation

1. Update your system packages:
```bash
sudo apt update && sudo apt upgrade
```

2. Install dependencies:
```bash
sudo apt install libssl-dev libudev-dev pkg-config zlib1g-dev llvm clang
```

3. Run the installation script:
```bash
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init_v1.16.6.sh)"
```

## 📋 Version Support

This repository supports multiple K2 network versions:
- v1.14.19
- v1.14.20
- v1.14.21
- v1.16.0 - v1.16.6 (Latest Stable)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a pull request

### Contribution Guidelines
- Follow existing script structure
- Ensure compatibility with K2 network requirements
- Include comments and documentation for changes

## 🔒 Security

- Always verify script contents before execution
- Use official sources for downloads
- Keep your system and dependencies updated

## 📜 License

Refer to the Koii Network official licensing terms.

## 🔗 Additional Resources

- [Koii Network Official Website](https://koii.network)
- [K2 Network Documentation](https://docs.koii.network)
- [Community Support](https://discord.gg/koii)

## 📞 Support

For technical support:
- Open a GitHub Issue
- Join the Koii Network Discord
- Email: support@koii.network