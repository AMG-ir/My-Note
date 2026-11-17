# Boot Process

How a Linux system goes from power-on to a running system, from the firmware stage to the first process.

## Boot Sequence

1. **Power-on and POST** (Power-On Self-Test): the firmware checks key hardware such as memory and CPU. On servers with many RAM slots, wrong module placement can make POST fail, and the server will not start.
2. **BIOS or UEFI**: initializes known hardware and decides the boot device (CD-ROM, USB flash, hard disk).
3. **Boot sector**: the firmware reads the boot information from the disk (MBR or GPT).
4. **Bootloader**: loads the kernel into memory.
5. **Kernel and initramfs**: the kernel starts with a lightweight temporary root filesystem (`initramfs`), then loads the remaining components.
6. **First process**: `init` / `systemd` starts as PID 1, then brings the system to the chosen runlevel.

## BIOS and UEFI

- Both can set the boot order and enable CPU features.
- **Intel VT / virtualization support** must be enabled in firmware if the machine will host virtual machines (hypervisor or workstation).
- **Hyper-Threading** lets one physical core appear as two logical cores. Whether it helps depends on the workload, so check the application's documentation before relying on it.
- **UEFI** is the newer firmware with a graphical interface and mouse support. **Secure Boot** is a UEFI feature and is not available with legacy BIOS.

## MBR and GPT

- **MBR** is the older partition scheme and has more limits.
- **GPT** is the newer scheme and needs UEFI.
- Partition count and size limits differ between the two. When initializing a new disk in Windows, you choose MBR or GPT first.

## Bootloaders

| Bootloader | Note |
|------------|------|
| LILO | Older Linux loader |
| GRUB (versions 2 and 3 mentioned) | Common loader, different versions have different features |

The bootloader loads the kernel into RAM so the system can start working.

## Kernel and initramfs

- During boot you will see `initramfs` messages.
- The kernel files are in `/boot`.
- A system can have several kernel versions installed side by side, each as its own set of files.

## init / systemd and PID 1

- The first process that starts is `init` (today usually `systemd`).
- Its PID is always **1**, and it is the parent of all other system processes.

## Runlevels

Runlevels are different operating states of the system. There are 7, from 0 to 6:

| Runlevel | State |
|----------|-------|
| 0 | Halt (shutdown) |
| 1 | Single-user mode |
| 2 | Multi-user |
| 3 | Multi-user with networking (text mode) |
| 4 | Custom, defined by the administrator |
| 5 | Graphical mode |
| 6 | Reboot |

- At runlevel 3 there is only a shell, no graphical interface.
- Graphical components (display managers and desktop environments such as GNOME or KDE) can be disabled or removed. On servers, no desktop is used.
- Reason: a graphical environment makes things easier for someone with access to the console, and it increases the attack surface.

## Key Takeaways

- The order is POST, firmware, boot sector, bootloader, kernel with initramfs, then PID 1.
- Virtualization support must be enabled in firmware before a virtualization host will work.
- On a server, disabling the graphical interface is a security habit.

## To Verify

- Exact limits of MBR and GPT (number of partitions and maximum disk size).
