# Linux Runlevels and systemd Targets

## Research Question

What are Linux runlevels, what does each traditional runlevel mean, and how can the system's operating state be changed?

## Purpose

Runlevels are a traditional way to describe the operating state of a Linux system. Understanding them is useful when learning Linux boot and service management, especially when comparing older SysVinit systems with modern systems that use systemd.

## 1. Traditional SysVinit Runlevels

On systems using SysVinit, runlevels are numbered from 0 to 6. Their exact meanings can vary by distribution, especially runlevels 2, 3, and 4.

| Runlevel | Traditional meaning |
| --- | --- |
| 0 | Halt / power off |
| 1 | Single-user or maintenance mode |
| 2 | Multi-user mode; details depend on the distribution |
| 3 | Multi-user mode, commonly without a graphical desktop |
| 4 | Usually unused or available for custom configuration |
| 5 | Multi-user mode with a graphical desktop on many distributions |
| 6 | Reboot |

These descriptions are common conventions, not a universal definition for every Linux distribution.

## 2. Runlevels on Modern systemd Systems

Modern distributions commonly use systemd rather than SysVinit. systemd uses **targets** to group units and define operating states. Some familiar runlevel names are provided as compatibility aliases, but runlevels and targets are not exactly the same concept.

| Traditional runlevel | Common systemd equivalent |
| --- | --- |
| 0 | `poweroff.target` |
| 1 | `rescue.target` |
| 2 | Often `multi-user.target`; distribution-dependent |
| 3 | `multi-user.target` |
| 4 | Often `multi-user.target`; distribution-dependent |
| 5 | `graphical.target` |
| 6 | `reboot.target` |

## 3. Check the Current or Default State

Show the previous and current runlevel when the compatibility command is available:

```bash
runlevel
```

On systemd systems, check the default target:

```bash
systemctl get-default
```

List active targets:

```bash
systemctl list-units --type=target
```

The default target describes the state systemd is configured to reach at startup; it does not necessarily tell you every target currently active.

## 4. Change the Current State

On a SysVinit system, the traditional commands include:

```bash
sudo init 3
```

or:

```bash
sudo telinit 3
```

These commands are for systems that support SysVinit runlevel switching; they are not the usual method on a modern systemd distribution.

On systemd, `systemctl isolate` switches to a target and starts its required units while stopping units not needed by that target, subject to the target's configuration.

Switch to a text-oriented multi-user state:

```bash
sudo systemctl isolate multi-user.target
```

Switch to a graphical state:

```bash
sudo systemctl isolate graphical.target
```

Switch to rescue mode:

```bash
sudo systemctl isolate rescue.target
```

**Caution:** isolating a target can stop services and may close the graphical session or interrupt remote access. Save your work first, and avoid doing this on a production or remote system unless you understand the impact.

For normal shutdown and restart, use the dedicated commands rather than isolating poweroff or reboot targets:

```bash
sudo systemctl poweroff
sudo systemctl reboot
```

## 5. Change the Default State at Boot

To make the system boot to a text-oriented multi-user state by default:

```bash
sudo systemctl set-default multi-user.target
```

To make it boot to the graphical state by default:

```bash
sudo systemctl set-default graphical.target
```

These commands change the default for future boots; they do not themselves switch the current session. Changing the default target can affect how the machine starts, so understand the system's intended use before changing it.

## 6. Key Distinctions

- **Runlevel:** the traditional numbered operating state used by SysVinit.
- **Target:** a systemd unit that groups other units and represents a desired state.
- **Current state:** what is active now.
- **Default target:** the state systemd is configured to reach during startup.

## Practical Verification

This note records concepts and example commands for study. No runlevel or systemd target change is claimed to have been performed or tested on a personal machine.

## Conclusion

Remember the traditional high-value associations: **0 = power off, 1 = maintenance, 3 = text-oriented multi-user mode, 5 = graphical mode, 6 = reboot**. On modern systemd distributions, learn the related targets—especially `rescue.target`, `multi-user.target`, and `graphical.target`—and remember that exact runlevel meanings vary by distribution.

## References

- [systemd.special(7) — Special systemd units](https://www.freedesktop.org/software/systemd/man/latest/systemd.special.html)
- [runlevel(8) — Print previous and current SysV runlevel](https://www.man7.org/linux/man-pages/man8/runlevel.8.html)
- [systemctl(1) — Control the systemd system and service manager](https://www.freedesktop.org/software/systemd/man/latest/systemctl.html)

---

Part of My-Note. Personal technical knowledge base, continuously updated.
