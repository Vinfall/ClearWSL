# ClearWSL
Clear Linux on WSL2 (Windows 10 FCU or later)
inspired by [ClearWSL](https://github.com/wight554/ClearWSL/)
based on [wsldl](https://github.com/yuk7/wsldl)

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
![License](https://img.shields.io/github/license/Vinfall/ClearWSL.svg?style=flat-square)

## Requirements
* Windows 10 Fall Creators Update x64 or later.
* Windows Subsystem for Linux feature is enabled.

## Install

1. Download installer zip from [release](https://github.com/Vinfall/ClearWSL/releases/latest) or [weekly action build](https://github.com/Vinfall/ClearWSL/actions/workflows/action.yml?query=is%3Asuccess) (recommended)
2. Extract all files in zip file to same directory (e.g. `C:\WSL\Clear`)
3. Run `Clear.exe` to Extract rootfs and Register to WSL

Exe filename is using to the instance name to register.
If you rename it, you can register with a different name and have multiple installs.

## How-to-Use(for Installed Instance)
#### exe Usage
```dos
Usage :
    <no args>
      - Open a new shell with your default settings.
    run <command line>
      - Run the given command line in that distro. Inherit current directory.
    config [setting [value]]
      - `--default-user <user>`: Set the default user for this distro to <user>
      - `--default-uid <uid>`: Set the default user uid for this distro to <uid>
      - `--append-path <on|off>`: Switch of Append Windows PATH to $PATH
      - `--mount-drive <on|off>`: Switch of Mount drives
    get [setting]
      - `--default-uid`: Get the default user uid in this distro
      - `--append-path`: Get on/off status of Append Windows PATH to $PATH
      - `--mount-drive`: Get on/off status of Mount drives
      - `--lxuid`: Get LxUID key for this distro
    backup
      - Output backup.tar.gz to the current directory using tar command.
      
    clean
      - Uninstall the distro.
    help
      - Print this usage message.
```


#### How to uninstall instance
```dos
>Clear.exe clean
```

## Todo

- [x] Add CI (GitHub Actions)
- [ ] Fix warning about `WSL (XX) ERROR: CreateProcessEntryCommon:XXX: getpwuid(0) failed 2`
