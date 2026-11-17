# Filesystem Hierarchy

The standard layout of directories in Linux and other UNIX-like systems. Knowing what each directory is for makes any Linux system easier to understand.

## Root

- `/` is the **root directory**: everything starts from it.
- `root` is the **administrator user** (similar to Administrator on Windows).
- `/root` is the home directory of the `root` user.
- These three are different things and should not be mixed up.
- Every user has a matching group. Members of the `root` group get the same access as the `root` user wherever the group is granted access.

## Main Directories

| Directory | Purpose |
|-----------|---------|
| `/bin` | Basic commands for all users (`ls`, `find`, and others) |
| `/sbin` | System administration commands (`reboot`, shutdown, and similar) |
| `/usr` | Large directory containing `bin`, `sbin`, libraries, and shared data |
| `/etc` | Configuration files for the system and services (SSH, NTP, and others) |
| `/home` | Personal data of each user, one directory per user |
| `/root` | Home of the `root` user, separate from `/home` for security |
| `/dev` | Devices shown as files |
| `/mnt` | Default place for manually mounted disks |
| `/media` | Removable media (CD-ROM, USB flash), mounted automatically |
| `/lib`, `/lib64` | Libraries needed by programs (32-bit and 64-bit) |
| `/tmp` | Temporary files, cleared on reboot |
| `/var` | Variable data such as logs and lock files |
| `/opt` | Optional third-party software (agents, monitoring tools) |
| `/boot` | Bootloader files and kernels |
| `/proc` | Running processes, one directory per PID |
| `/sys` | Hardware-related information and kernel interaction |
| `/run` | Runtime data of running programs (sockets, PID files) |

## Commands: `/bin` and `/sbin`

- Commands for normal work (such as `ls` and `find`) are in `/bin`.
- System-wide actions (such as `reboot`) are in `/sbin`, because they affect the whole system rather than only one user session.

## Devices as Files

- Linux treats every device as a file under `/dev`.
- Disks are named with letters and partitions with numbers:

| Name | Meaning |
|------|---------|
| `sda` | First disk |
| `sdb` | Second disk |
| `sda1` | First partition of the first disk |
| `sdb5` | Fifth partition of the second disk |

- A device that firmware has detected will appear in the device list, for example with `lspci`.
- This design lets you see which CPU core and which memory a program used.

## Processes in `/proc`

- Each running process gets a directory named after its PID.
- The directory exists as long as the process runs, and is removed when it ends.

## Libraries

- A library is a collection of ready-made functions that programs call, similar to looking a word up in a dictionary instead of writing the definition again.
- For example, programs that use networking get TCP/IP functions from libraries.
- 32-bit and 64-bit libraries are kept separately (`lib` and `lib64`).
- The name x86 comes from the Intel CPU family numbers (8086, 80186, 80386).

## Key Takeaways

- `/` is the root of the filesystem, `root` is the administrator, `/root` is that user's home.
- Settings live in `/etc`, user data in `/home`, logs and changing data in `/var`.
- Devices appear as files in `/dev`, processes appear as directories in `/proc`.

## To Verify

- Details of `/sys` and `/run` will be checked again when they come up in later sessions.
