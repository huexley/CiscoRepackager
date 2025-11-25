# Cisco Secure Client Repackager

A macOS utility to repackage Cisco Secure Client DMG files for unattended deployment via Jamf Pro (or any MDM solution).

![macOS](https://img.shields.io/badge/macOS-15.0%2B-blue)
![Swift](https://img.shields.io/badge/Swift-6.0-orange)
![License](https://img.shields.io/badge/License-MIT-green)

## Features

- **Drag & Drop** - Simply drop your Cisco Secure Client DMG
- **Module Selection** - Choose which modules to include in your deployment package
- **Clean UI** - Modern SwiftUI interface with step-by-step workflow
- **No Signing Required** - Output PKG works without code signing for internal deployment

## Supported Modules

- AnyConnect VPN
- Secure Firewall Posture (ISE Posture)
- AMP Enabler
- Network Visibility Module (NVM)
- Umbrella Roaming Security
- Duo Security
- Zero Trust Access (ZTNA)
- ThousandEyes
- DART (Diagnostic and Reporting Tool)

## Requirements (tested with, may work with previous versions of macOS)

- macOS 25.0 (Tahoe) or later
- Xcode 16.0 or later (for building from source)

## Installation

### From Source

1. Clone this repository:
   ```bash
   git clone https://github.com/huexley/CiscoRepackager.git
   ```

2. Open in Xcode:
   ```bash
   cd CiscoRepackager
   open CiscoRepackager.xcodeproj
   ```

3. Build and run (⌘R)

## Usage

1. **Drop your DMG** - Drag the official Cisco Secure Client DMG onto the app window
2. **Click Continue** - The app will mount, extract, and parse the package
3. **Select modules** - Check/uncheck the modules you want to include
4. **Build PKG** - Click the green "Build PKG" button and choose where to save

The resulting PKG can be deployed silently via Jamf Pro or any other MDM solution.

## How It Works

1. Mounts the Cisco Secure Client DMG
2. Expands the `Cisco Secure Client.pkg` using `pkgutil --expand`
3. Parses the `Distribution` XML file to find available modules
4. Filters the Distribution file based on your selection
5. Flattens the package back using `pkgutil --flatten`

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Yannick Housseau**
- GitHub: [@huexley](https://github.com/huexley)

## Contributing

Contributions are welcome! Feel free to:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Acknowledgments

- Built for the Mac Admin community
- Inspired by the need to simplify Cisco Secure Client deployments
