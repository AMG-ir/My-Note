Linux Command Line

«Notes, commands, and practical examples from my Linux system administration studies.»

---

📌 Overview

The Linux command line is one of the core tools for system administration.
This section covers basic navigation, file and directory management, privilege handling, command history, and command documentation.

---

🧭 Navigation

pwd — Print Working Directory

Displays the absolute path of the current working directory.

```bash
pwd
```

ls — List Directory Contents

Lists files and directories.

```bash
ls
ls -l
ls -la
```

Option Description
-l Long listing format
-a Show hidden files
-la Combine both options

cd — Change Directory

Moves to another directory.

```bash
cd /path/to/directory
cd ..
cd ~
```

Command Purpose
cd /path Go to a specific directory
cd .. Move to the parent directory
cd ~ Move to the user's home directory

---

📁 Files & Directories

mkdir — Create a Directory

```bash
mkdir directory_name
mkdir -p parent/child
```

The -p option creates parent directories when they do not already exist.

rmdir — Remove an Empty Directory

```bash
rmdir directory_name
```

«"rmdir" only removes empty directories.»

rm — Remove Files or Directories

```bash
rm file.txt
rm -r directory_name
```

«⚠️ Be careful with "rm -r". It can recursively remove a directory and its contents.»

truncate — Change File Size

Creates an empty file or changes the size of an existing file.

```bash
truncate -s 0 file.txt
truncate -s 100M file.img
```

---

🔐 Privilege Management

sudo -i — Start a Root Shell

Opens a root login shell using sudo.

```bash
sudo -i
```

«Use root privileges only when necessary.»

---

🕘 Command History

history

Displays previously executed commands.

```bash
history
```

A specific command can be executed by its history number:

```bash
!300
```

This executes command number "300" from the current shell's history.

---

📖 Getting Help

man — Manual Pages

Displays the manual page for a command.

```bash
man ls
man systemctl
```

Manual pages are one of the most important built-in references when working with Linux.

which — Locate an Executable

Shows the executable that would be found through the current PATH.

```bash
which python3
which ls
```

whereis — Locate Related Files

Searches for the binary, source, and manual pages associated with a command.

```bash
whereis ls
whereis bash
```

---

🧠 Key Takeaways

· Linux administration heavily relies on the command line.
· Understanding paths and directory navigation is fundamental.
· man is an essential source of documentation.
· sudo provides controlled access to privileged operations.
· Commands such as rm should be used carefully, especially with recursive options.

---

🧪 Practice

The commands in this section were studied and practiced as part of my Linux system administration learning.

Current focus: Building confidence with everyday command-line operations and understanding how Linux commands behave in practical environments.

