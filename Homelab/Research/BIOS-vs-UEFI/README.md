# BIOS vs. UEFI

## Research Question

How do legacy BIOS and UEFI differ in the way a computer initializes hardware and starts an operating system?

## Purpose

Understand the firmware boot process and recognize how firmware mode affects operating-system installation and boot troubleshooting.

## Background

Firmware is low-level software stored on a system's motherboard or platform firmware chip. It runs before the operating system and initializes enough of the system to begin the boot process.

**BIOS** (Basic Input/Output System) refers to the legacy PC firmware interface. **UEFI** (Unified Extensible Firmware Interface) is a newer, standardized firmware interface designed to provide a more flexible boot environment.

Both BIOS-based and UEFI-based systems perform hardware initialization and may carry out POST (Power-On Self-Test) checks. POST is not exclusive to legacy BIOS.

## Findings

### Legacy BIOS boot

A typical legacy BIOS boot sequence is:

1. The computer powers on and firmware initializes essential hardware and performs early checks.
2. The firmware selects a boot device according to its boot order.
3. Legacy boot code is loaded from the device's boot sector, commonly the MBR on a partitioned hard drive.
4. That code transfers control to a bootloader, which continues loading the operating system.

The exact sequence varies by firmware and boot device.

### UEFI boot

A typical UEFI boot sequence is:

1. The computer powers on and UEFI firmware initializes platform hardware and performs early checks.
2. Firmware uses its boot configuration to select a boot option.
3. For a normal disk-based UEFI installation, firmware launches an EFI executable from the EFI System Partition (ESP).
4. The bootloader loads or starts the operating system.

The ESP is commonly formatted as FAT32. On Linux, it may be mounted at a path such as `/boot/efi` or `/boot`, depending on the distribution and configuration.

### Main differences

| Feature | Legacy BIOS | UEFI |
| --- | --- | --- |
| Boot mechanism | Executes legacy boot code from a boot device, commonly the MBR boot sector | Can launch EFI applications identified by firmware boot entries |
| Typical disk layout | Often paired with MBR | Often paired with GPT |
| Boot configuration | Usually relies on device boot order and legacy boot code | Can store named boot entries and EFI executable paths |
| Extensibility | More limited legacy interface | Defined services and extensible EFI applications and drivers |
| Secure Boot | Does not provide the UEFI Secure Boot mechanism | Can support Secure Boot when supported and configured |
| User interface | Often text-based | May be text-based or graphical; a graphical interface is not guaranteed |

BIOS/UEFI and MBR/GPT are related in common setups, but they are not the same category of technology. The pairing is typical rather than an absolute rule.

### Secure Boot

UEFI can support Secure Boot, which uses trust keys and signature verification policies to help prevent unauthorized boot components from running. Secure Boot is not necessarily enabled on every UEFI system, and it does not protect against every type of malware.

## Practical Verification

On Linux, this command checks whether the currently running system was booted through UEFI:

```bash
test -d /sys/firmware/efi && echo UEFI || echo BIOS/Legacy
```

If the directory exists, the running environment was generally booted in UEFI mode. If it does not exist, the system may have been booted in legacy mode. This checks the current boot mode, not every capability supported by the motherboard.

This note documents research and example commands. No firmware settings were changed and no installation test is claimed.

## Conclusion

Both legacy BIOS and UEFI initialize hardware and begin the operating-system boot process, and both may perform POST checks. UEFI provides a more flexible boot architecture and supports features such as EFI boot applications and Secure Boot. On modern computers, UEFI with GPT is common, but the actual supported mode depends on the system and its configuration.

## References

- [UEFI Forum](https://uefi.org/)
- [UEFI Specification](https://uefi.org/specifications)
- [Microsoft Learn: Windows and GPT FAQ](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-and-gpt-faq)
- [Linux manual: efivarfs](https://man7.org/linux/man-pages/man5/efivarfs.5.html)
