# MBR vs. GPT

## Research Question

How do MBR and GPT differ, and how do they relate to BIOS and UEFI boot modes?

## Purpose

Understand disk partition-table formats used when preparing storage for operating-system installation and troubleshooting boot problems.

## Background

A partition table describes how a disk is divided into partitions. **MBR** (Master Boot Record) and **GPT** (GUID Partition Table) are two partitioning schemes.

They are not firmware types: BIOS and UEFI describe firmware/boot interfaces, while MBR and GPT describe disk partition-table layouts.

## Findings

### MBR (Master Boot Record)

MBR is a legacy partitioning scheme. On a typical MBR-partitioned disk:

- The MBR is located in the first logical sector and contains boot code and partition-table information.
- The partition table supports up to four primary partition entries.
- To create more than four partitions, one entry is commonly used for an extended partition containing logical partitions.
- With traditional 512-byte logical sectors and standard addressing, the common maximum addressable disk size is about 2 TiB (often marketed as 2 TB).

MBR has limited redundancy: its main partition-table information is not backed up in a separate location in the way GPT's is.

### GPT (GUID Partition Table)

GPT is a newer partitioning scheme commonly used with UEFI systems. It typically provides:

- Support for disks much larger than the traditional MBR limit.
- Many partitions without the MBR primary/extended/logical distinction; the practical limit depends on the operating system and implementation.
- A primary GPT header and partition-entry array, plus backup copies near the end of the disk.
- CRC checks to help detect corruption in GPT metadata.

GPT disks also normally contain a protective MBR, which helps legacy disk tools recognize that the disk is in use. The protective MBR does not make a disk a normal legacy-MBR partitioned disk.

### Comparison

| Feature | MBR | GPT |
| --- | --- | --- |
| Full name | Master Boot Record | GUID Partition Table |
| Typical association | Legacy BIOS systems | UEFI systems |
| Partition count | Four primary entries, or extended/logical partitioning | Many partitions; exact limit depends on implementation |
| Typical size limit | About 2 TiB with traditional 512-byte logical sectors | Much larger; practical limits depend on implementation |
| Metadata redundancy | Limited | Primary and backup partition metadata |
| Integrity checks | No comparable built-in CRC scheme for the partition table | CRC checks for GPT structures |
| Modern deployment | Used for legacy compatibility | Common choice for modern systems |

### How MBR/GPT relate to BIOS/UEFI

- **UEFI + GPT** is the common setup for modern operating-system installations.
- **Legacy BIOS + MBR** is a common older setup.
- Some systems and operating systems support other combinations, so do not assume that the firmware mode alone proves which partition table a disk uses.

For a typical UEFI-based Windows installation, the system disk is expected to use GPT. Requirements differ across operating systems and installation methods.

## Practical Verification

On Linux, the following command lists disks and their partition-table type:

```bash
sudo fdisk -l
```

Depending on the tool version, the output identifies a disk label such as `dos` (MBR) or `gpt`.

Alternatively, `parted -l` can display disk partition-table information if GNU Parted is installed.

These are inspection examples only. No disk was modified, and no partitioning or installation test is claimed. Be careful: partitioning and formatting commands can destroy data.

## Conclusion

MBR and GPT are partition-table formats, not BIOS/UEFI modes. MBR has legacy limits on partition count and addressable disk size. GPT supports much larger disks, more partitions, and redundant metadata with integrity checks. UEFI with GPT is common on modern computers, while BIOS with MBR is common on older systems.

## References

- [Microsoft Learn: Windows and GPT FAQ](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-and-gpt-faq)
- [GNU Parted Manual](https://www.gnu.org/software/parted/manual/)
- [UEFI Specification](https://uefi.org/specifications)
- [Linux manual: fdisk](https://man7.org/linux/man-pages/man8/fdisk.8.html)
