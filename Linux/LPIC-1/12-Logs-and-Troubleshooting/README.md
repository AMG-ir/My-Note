# 12 - Logs and Troubleshooting

This section covers basic Linux logs, system information, hardware inspection, and troubleshooting techniques.

## Overview

Linux systems keep logs that help identify errors, warnings, and system events.

Logs can be useful when troubleshooting problems with:

- Services
- Hardware
- Processes
- Networking
- System startup
- User activity

System logs can be inspected using `journalctl`.

## Contents

- [journalctl](#journalctl)
- [/proc](#proc)
- [/dev](#dev)
- [/sys](#sys)
- [Hardware Information](#hardware-information)
- [Hashing](#hashing)
- [Basic Troubleshooting Workflow](#basic-troubleshooting-workflow)
- [Example: Troubleshooting a Service](#example-troubleshooting-a-service)
- [Example: Hardware Troubleshooting](#example-hardware-troubleshooting)
- [Useful Commands](#useful-commands)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## journalctl

`journalctl` is used to view logs collected by systemd.

### View Logs

```bash
journalctl
```

### View the Latest Entries

```bash
journalctl -n
```

### Follow Logs in Real Time

```bash
journalctl -f
```

### View Logs for a Specific Service

```bash
journalctl -u ssh
```

### Follow Logs for a Specific Service

```bash
journalctl -u ssh -f
```

These commands are especially useful when troubleshooting systemd services.

---

## /proc

`/proc` is a virtual filesystem that provides information about the running system and processes.

```bash
ls /proc
```

Process information can be found inside directories named with process IDs.

```text
/proc/1
/proc/100
/proc/500
```

The directory name represents the PID of the process.

---

## /dev

`/dev` contains device files representing hardware and other system devices.

```bash
ls /dev
```

Storage devices can appear with names such as:

```text
/dev/sda
/dev/sdb
```

Partitions may appear as:

```text
/dev/sda1
/dev/sda2
```

---

## /sys

`/sys` is a virtual filesystem that exposes information about devices, hardware, and the kernel.

```bash
ls /sys
```

It can be useful when investigating hardware and device-related information.

---

## Hardware Information

### lspci

Displays information about PCI devices.

```bash
lspci
```

It can be useful for identifying hardware such as:

- Network controllers
- Graphics controllers
- Audio controllers
- Storage controllers

### lshw

Displays detailed information about the system hardware.

```bash
lshw
```

It can be useful when checking the hardware configuration of a Linux system.

---

## Hashing

Hashing can be used to calculate a checksum for a file.

### MD5

```bash
md5sum file.txt
```

### SHA-256

```bash
sha256sum file.txt
```

The resulting hash can be compared with another hash to check whether the file contents match.

---

## Basic Troubleshooting Workflow

When a problem occurs, start by identifying what is affected. A basic troubleshooting process can be:

1. Identify the problem.
2. Check whether a process is involved.
3. Check relevant system or service logs.
4. Check hardware information when necessary.
5. Inspect the relevant system area such as `/proc`, `/dev`, or `/sys`.
6. Compare the current state with the expected state.
7. Make one change at a time.
8. Check the result.

---

## Example: Troubleshooting a Service

Check the service status:

```bash
systemctl status service-name
```

Check its logs:

```bash
journalctl -u service-name
```

Follow the logs while testing:

```bash
journalctl -u service-name -f
```

This helps determine whether the problem is related to the service itself.

---

## Example: Hardware Troubleshooting

When investigating a hardware-related problem, hardware information can be checked with:

```bash
lspci
```

and:

```bash
lshw
```

Additional system and device information can be inspected through:

```text
/proc
/dev
/sys
```

---

## Useful Commands

| Command / Path   | Purpose |
|------------------|---------|
| `journalctl`     | View system logs |
| `journalctl -n`  | View recent log entries |
| `journalctl -f`  | Follow logs in real time |
| `journalctl -u`  | View logs for a service |
| `lspci`          | Display PCI hardware information |
| `lshw`           | Display hardware information |
| `md5sum`         | Calculate an MD5 hash |
| `sha256sum`      | Calculate a SHA-256 hash |
| `/proc`          | Runtime system and process information |
| `/dev`           | Device files |
| `/sys`           | Hardware and kernel information |

---

## Key Takeaways

- Logs are an important source of information when troubleshooting Linux systems.
- `journalctl` is used to inspect systemd logs.
- `/proc` provides information about running processes and the system.
- `/dev` contains device files.
- `/sys` provides information about devices and the kernel.
- `lspci` and `lshw` can be used to inspect hardware.
- `md5sum` and `sha256sum` can be used to calculate file hashes.
- Troubleshooting should be systematic rather than based on random changes.

---

## Practice

### View the Latest System Log Entries

```bash
journalctl -n
```

### Follow System Logs in Real Time

```bash
journalctl -f
```

### Display PCI Devices

```bash
lspci
```

### Display Hardware Information

```bash
lshw
```

### Calculate the SHA-256 Hash of a File

```bash
sha256sum file.txt
```

### Explore System Directories

```bash
ls /proc
ls /dev
ls /sys
```

---

Part of My-Note. Personal technical knowledge base, continuously updated.
