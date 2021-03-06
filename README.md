# M1-Linux-SSH
Apple M1 Linux VM with SSH interface

# Usage

## Host

- Download a Linux ARM distribution such as `focal-desktop-arm64.iso`
- Extract vmlinuz and initrd following this:
    1. `sudo mkdir /Volumes/Ubuntu`
    2. `sudo hdiutil attach -nomount /path/to/your/downloaded.iso`
    3. `sudo mount -t cd9660 /dev/diskX /Volumes/Ubuntu` (X is what the FDisk_partition_scheme from step 2)
    4. `open /Volumes/Ubuntu/casper`
    5. Copy `vmlinuz` and `initrd` to your own folder
    6. Rename `vmlinuz` to `vmlinuz.gz` and unarchive it
- Build and call the service passing path to iso and extracted vmlinuz and initrd files

```
USAGE: vm-service <linux-path> <vmlinuz-path> <initrd-path> [--ip <ip>] [--port <port>] [--username <username>] [--password <password>]

ARGUMENTS:
  <linux-path>            Path to the Linux ISO file.
  <vmlinuz-path>          Path to the vmlinuz file.
  <initrd-path>           Path to the initrd file.

OPTIONS:
  --ip <ip>               IP Address. (default: 0.0.0.0)
  --port <port>           Port. (default: 2222)
  --username <username>   SSH Username.
  --password <password>   SSH Password.
  -h, --help              Show help information.
```

## Client
```bash
ssh 0.0.0.0 -p 2222
```

## Credits

This project use the [Apple SwiftNIO SSH package](https://github.com/apple/swift-nio-ssh) and it is strongly inspired by the work done by Khaos Tian with the [SimpleVM project](https://github.com/KhaosT/SimpleVM)
