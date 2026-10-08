# 06 - Systemd

This section covers the basic concepts and commands used to manage services and system processes with systemd.

## Overview

`systemd` is the system and service manager used by many modern Linux distributions. It manages services and other system units and can control their state during system operation.

The main command used to interact with systemd is `systemctl`.

## Contents

- [systemctl](#systemctl)
- [Service Management](#service-management)
- [Checking Service State](#checking-service-state)
- [Listing Units](#listing-units)
- [Unit Files](#unit-files)
- [journalctl](#journalctl)
- [Combining systemctl and journalctl](#combining-systemctl-and-journalctl)
- [Common Service Management Commands](#common-service-management-commands)
- [Common Journal Commands](#common-journal-commands)
- [Practical Examples](#practical-examples)
- [Troubleshooting Workflow](#troubleshooting-workflow)
- [Key Takeaways](#key-takeaways)

---

## systemctl

`systemctl` is used to manage and inspect systemd services and units.

Basic syntax:

```bash
systemctl [command] [unit]
```

---

## Service Management

### Checking Service Status

Use `systemctl status` to check the current status of a service.

```bash
systemctl status service-name
```

Example:

```bash
systemctl status ssh
```

The output provides information about the service, including whether it is currently running.

### Starting a Service

```bash
sudo systemctl start service-name
```

Example:

```bash
sudo systemctl start ssh
```

Starting a service affects its current state.

### Stopping a Service

```bash
sudo systemctl stop service-name
```

Example:

```bash
sudo systemctl stop ssh
```

### Restarting a Service

Stops and starts a service again.

```bash
sudo systemctl restart service-name
```

Example:

```bash
sudo systemctl restart ssh
```

Restarting a service is useful when a configuration change needs to be applied.

### Enabling a Service

A service can be enabled so that it starts automatically during system boot.

```bash
sudo systemctl enable service-name
```

Example:

```bash
sudo systemctl enable ssh
```

### Disabling a Service

Prevents a service from being automatically started during boot.

```bash
sudo systemctl disable service-name
```

Example:

```bash
sudo systemctl disable ssh
```

### Enable and Start

A service can be enabled and started at the same time.

```bash
sudo systemctl enable --now service-name
```

Example:

```bash
sudo systemctl enable --now ssh
```

### Disable and Stop

A service can be disabled and stopped at the same time.

```bash
sudo systemctl disable --now service-name
```

Example:

```bash
sudo systemctl disable --now ssh
```

### Masking a Service

`mask` prevents a service from being started.

```bash
sudo systemctl mask service-name
```

Example:

```bash
sudo systemctl mask ssh
```

> **Note:** A masked service cannot normally be started until it is unmasked.

### Unmasking a Service

Removes the mask from a service.

```bash
sudo systemctl unmask service-name
```

Example:

```bash
sudo systemctl unmask ssh
```

---

## Checking Service State

### Checking Whether a Service Is Enabled

```bash
systemctl is-enabled service-name
```

Example:

```bash
systemctl is-enabled ssh
```

### Checking Whether a Service Is Active

```bash
systemctl is-active service-name
```

Example:

```bash
systemctl is-active ssh
```

---

## Listing Units

`systemctl` can be used to view systemd units.

```bash
systemctl list-units
```

The output shows currently loaded units.

To list only service units:

```bash
systemctl list-units --type=service
```

---

## Unit Files

systemd uses unit files to define how different units are managed. Service unit files commonly use the `.service` extension.

```text
example.service
```

Unit files contain configuration information used by systemd.

### Viewing a Unit File

```bash
systemctl cat service-name
```

Example:

```bash
systemctl cat ssh
```

This displays the unit file configuration used by the service.

### Reloading systemd Configuration

When unit files are changed, systemd can reload its configuration with:

```bash
sudo systemctl daemon-reload
```

---

## journalctl

`journalctl` is used to view logs collected by the systemd journal.

Basic usage:

```bash
journalctl
```

### Viewing Recent Logs

```bash
journalctl -n
```

This displays recent journal entries.

### Following Logs

Use `-f` to follow new log entries as they are generated.

```bash
journalctl -f
```

This is useful when monitoring a service while it is running.

### Viewing Logs for a Service

Use `-u` to display logs for a specific unit.

```bash
journalctl -u service-name
```

Example:

```bash
journalctl -u ssh
```

To follow the logs of a service:

```bash
journalctl -u ssh -f
```

---

## Combining systemctl and journalctl

`systemctl` can be used to check the current state of a service:

```bash
systemctl status ssh
```

`journalctl` can then be used to inspect its logs:

```bash
journalctl -u ssh
```

This combination is useful when troubleshooting service problems.

---

## Common Service Management Commands

| Command                       | Purpose |
|-------------------------------|---------|
| `systemctl status`            | Check service status |
| `systemctl start`             | Start a service |
| `systemctl stop`              | Stop a service |
| `systemctl restart`           | Restart a service |
| `systemctl enable`            | Enable a service at boot |
| `systemctl disable`           | Disable a service at boot |
| `systemctl mask`              | Prevent a service from being started |
| `systemctl unmask`            | Remove a service mask |
| `systemctl is-enabled`        | Check whether a service is enabled |
| `systemctl is-active`         | Check whether a service is active |
| `systemctl list-units`        | List loaded units |
| `systemctl cat`               | Display a unit file |
| `systemctl daemon-reload`     | Reload systemd unit configuration |

---

## Common Journal Commands

| Command          | Purpose |
|------------------|---------|
| `journalctl`     | View system journal logs |
| `journalctl -n`  | View recent log entries |
| `journalctl -f`  | Follow new log entries |
| `journalctl -u`  | View logs for a specific unit |

---

## Practical Examples

### Check a Service

```bash
systemctl status ssh
```

### Start a Service

```bash
sudo systemctl start ssh
```

### Stop a Service

```bash
sudo systemctl stop ssh
```

### Restart a Service

```bash
sudo systemctl restart ssh
```

### Enable a Service

```bash
sudo systemctl enable ssh
```

### Disable a Service

```bash
sudo systemctl disable ssh
```

### Mask a Service

```bash
sudo systemctl mask ssh
```

### Unmask a Service

```bash
sudo systemctl unmask ssh
```

### View Service Logs

```bash
journalctl -u ssh
```

### Follow Service Logs

```bash
journalctl -u ssh -f
```

### View a Unit File

```bash
systemctl cat ssh
```

---

## Troubleshooting Workflow

When a service is not working, a basic workflow is:

1. Check the service status:

   ```bash
   systemctl status service-name
   ```

2. Check the service logs:

   ```bash
   journalctl -u service-name
   ```

3. Restart the service:

   ```bash
   sudo systemctl restart service-name
   ```

4. Check the status again:

   ```bash
   systemctl status service-name
   ```

---

## Key Takeaways

- systemd manages services and system units.
- `systemctl` is used to control and inspect services.
- `start`, `stop`, and `restart` control the current service state.
- `enable` and `disable` control whether a service starts automatically.
- `mask` prevents a service from being started.
- `journalctl` is used to view systemd journal logs.
- `systemctl status` and `journalctl` are useful together when troubleshooting services.
- Unit files define how systemd manages services and other units.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
