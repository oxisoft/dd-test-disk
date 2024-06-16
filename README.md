# Disk Test Script - Run Without Installation

This script is designed to test the disk performance by writing and reading a 1 GB file. It can be run directly from the internet without installation.

## Prerequisites

- The script requires `sudo` permissions to clear the system cache before each test.
- The `dd` utility is already installed on all Unix-like systems.

## How to Use

You can run the script directly from GitHub using the following command:

```sh
curl -sL https://raw.githubusercontent.com/oxisoft/dd-test-disk/main/disk-test.sh | sudo bash -s /path/to/folder
```

Replace `/path/to/folder` with the actual folder path where you want to perform the disk test.

### Example

```sh
curl -sL https://raw.githubusercontent.com/oxisoft/dd-test-disk/main/disk-test.sh | sudo bash -s /tmp/testdisk
```

## License

This project is created by [OxiSoft.io](https://oxisoft.io) and is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
