# ClearWSL
Clear Linux OS on WSL2 (Windows 10 FCU or later)
inspired by [ClearWSL](https://github.com/wight554/ClearWSL/)
based on [wsldl](https://github.com/yuk7/wsldl).

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
![License](https://img.shields.io/github/license/Vinfall/ClearWSL.svg?style=flat-square)

**Notice: This is *Clear Linux OS* backed by Intel. Not to be confused with *Clear OS*, which is a completely different CentOS/RHEL-based distro.**

## Requirements
* Windows 10 Fall Creators Update x64 or later.
* Windows Subsystem for Linux feature is enabled.

## Install

1. Download installer zip from [release](https://github.com/Vinfall/ClearWSL/releases/latest) or [weekly action build](https://github.com/Vinfall/ClearWSL/releases/tag/action-build) (recommended)
2. Extract all files in zip file to same directory (e.g. `C:\WSL\Clear`)
3. Run `Clear.exe` to Extract rootfs and Register to WSL

Exe filename is using to the instance name to register.
If you rename it, you can register with a different name and have multiple installs.

## Init

For now there would be a warning `WSL (XX) ERROR: CreateProcessEntryCommon:XXX: getpwuid(0) failed 2` during startup, but it's harmless despite annoying.
I will accept and appreciate it if anyone opens a PR regarding this!

By default, ClearWSL comes with no `sudo` package.
To install `sudo` and make it function properly:
```sh
# Create /etc/passwd as it's not available by default
passwd
# Install `sudo`
swupd bundle-add --assume=yes sudo
# Check update
sudo swupd check-update
# Update
sudo swupd update
```

## Telemetrics

It's worth mentioning that Clear Linux OS has a [built-in telemetry function](https://clearlinux.github.io/clear-linux-documentation/guides/clear/telemetrics.html) and **opt-in** by default. In ClearWSL the client is *not* active (maybe due to the fact that SystemD needs to be explicitly enabled in `/etc/wsl.conf`).

If you use SystemD, it's better to ensure the telemetrics are disabled if you don't want this feature:
```sh
# Disabling after install
sudo telemctl stop
# Opt out of telemetry
sudo telemctl opt-out
```

If you get `sudo: telemctl: command not found`, it means that you don't have `telemetrics` bundle installed, so no worries about telemetry.

For further information, please read [the official documentation for Clear Linux* Project](https://clearlinux.github.io/clear-linux-documentation/guides/clear/telemetrics.html#id9).

## How-to-Use (for Installed Instance)

### exe Usage
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

### How to uninstall instance
```dos
>Clear.exe clean
```

## Todo

- [x] Add CI (GitHub Actions)
- [ ] Fix warning about `WSL (XX) ERROR: CreateProcessEntryCommon:XXX: getpwuid(0) failed 2` according to [microsoft/WSL#5923]([url](https://github.com/microsoft/WSL/issues/5923#issuecomment-1684949247)https://github.com/microsoft/WSL/issues/5923#issuecomment-1684949247) or another issue I forgot to take note, or do some dirty hack on `/etc/fstab` or `/etc/wsl.conf`
