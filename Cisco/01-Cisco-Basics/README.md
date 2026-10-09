# 01 - Cisco Basics

This section covers the basic concepts and initial configuration of Cisco networking devices.

## Cisco IOS

Cisco IOS is an operating system used on many Cisco networking devices, including routers and switches.

## Command Modes

The Cisco IOS CLI provides different command modes.

| Mode                    | Purpose |
|-------------------------|---------|
| User EXEC               | Basic device access and limited commands |
| Privileged EXEC         | Access to administrative and diagnostic commands |
| Global Configuration    | Configure device-wide settings |
| Interface Configuration | Configure a specific interface |

## Basic CLI Commands

| Command                              | Purpose |
|--------------------------------------|---------|
| `enable`                             | Enter Privileged EXEC mode |
| `configure terminal`                 | Enter Global Configuration mode |
| `hostname <name>`                    | Set the device hostname |
| `show running-config`                | Display the active configuration |
| `show startup-config`                | Display the saved configuration |
| `copy running-config startup-config` | Save the current configuration |

## Basic Configuration Workflow

```text
enable
configure terminal
hostname Switch1
end
copy running-config startup-config
```

This example changes the device hostname and saves the configuration.

## Notes

- `running-config` represents the active configuration in memory.
- `startup-config` is the configuration used when the device starts.
- Configuration commands are entered in the appropriate CLI mode.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
