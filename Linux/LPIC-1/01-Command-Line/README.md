# 01 - Command Line

Notes, commands, and practical examples from my Linux system administration studies.

## Overview

The Linux command line is one of the core tools for system administration. This section covers basic navigation, file and directory management, privilege handling, command history, and command documentation.

## Contents

- [Navigation](#navigation)
- [Files and Directories](#files-and-directories)
- [Privilege Management](#privilege-management)
- [Command History](#command-history)
- [Getting Help](#getting-help)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## Navigation

### pwd

Prints the absolute path of the current working directory.

```bash
pwd
```

### ls

Lists files and directories.

```bash
ls
ls -l
ls -la
```

| Option | Description |
|--------|-------------|
| `-l`   | Long listing format |
| `-a`   | Show hidden files |
| `-la`  | Combine both options |

### cd

Changes the current directory.

```bash
cd /path/to/directory
cd ..
cd ~
```

| Command    | Purpose |
|------------|---------|
| `cd /path` | Go to a specific directory |
| `cd ..`    | Move to the parent directory |
| `cd ~`     | Move to the user's home directory |

---

## Files and Directories

### mkdir

Creates a directory.

```bash
mkdir directory_name
mkdir -p parent/child
```

The `-p` option creates parent directories when they do not already exist.

### rmdir

Removes an empty directory.

```bash
rmdir directory_name
```

> **Note:** `rmdir` only removes empty directories.

### rm

Removes files or directories.

```bash
rm file.txt
rm -r directory_name
```

> **Warning:** Be careful with `rm -r`. It recursively removes a directory and its contents.

### truncate

Creates an empty file or changes the size of an existing file.

```bash
truncate -s 0 file.txt
truncate -s 100M file.img
```

---

## Privilege Management

### sudo -i

Opens a root login shell using `sudo`.

```bash
sudo -i
```

> **Note:** Use root privileges only when necessary.

---

## Command History

### history

Displays previously executed commands.

```bash
history
```

A specific command can be executed by its history number:

```bash
!300
```

This executes command number 300 from the current shell's history.

---

## Getting Help

### man

Displays the manual page for a command.

```bash
man ls
man systemctl
```

Manual pages are one of the most important built-in references when working with Linux.

### which

Shows the executable that would be found through the current `PATH`.

```bash
which python3
which ls
```

### whereis

Searches for the binary, source, and manual pages associated with a command.

```bash
whereis ls
whereis bash
```

---

## Key Takeaways

- Linux administration relies heavily on the command line.
- Understanding paths and directory navigation is fundamental.
- `man` is an essential source of documentation.
- `sudo` provides controlled access to privileged operations.
- Commands such as `rm` should be used carefully, especially with recursive options.

## Practice

The commands in this section were studied and practiced as part of my Linux system administration learning.

Current focus: building confidence with everyday command-line operations and understanding how Linux commands behave in practical environments.
