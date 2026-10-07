Linux Command Line

«Notes, commands, and practical examples from my Linux system administration studies.»

---

📌 Overview

The Linux command line is one of the core tools for system administration.

This section covers:

- Basic navigation
- File and directory management
- Privilege management
- Command history
- Command documentation
- Basic command discovery

---

🧭 Navigation

"pwd" — Print Working Directory

Displays the absolute path of the current working directory.

pwd

"ls" — List Directory Contents

Lists files and directories.

ls
ls -l
ls -la

Option| Description
"-l"| Long listing format
"-a"| Show hidden files
"-la"| Combine both options

"cd" — Change Directory

Moves to another directory.

cd /path/to/directory
cd ..
cd ~

Command| Purpose
"cd /path"| Go to a specific directory
"cd .."| Move to the parent directory
"cd ~"| Move to the user's home directory

---

📁 Files & Directories

"mkdir" — Create a Directory

Creates a new directory.

mkdir directory_name

The "-p" option can be used to create parent directories when needed.

mkdir -p parent/child

"rmdir" — Remove an Empty Directory

rmdir directory_name

«"rmdir" only removes empty directories.»

"rm" — Remove Files or Directories

Remove a file:

rm file.txt

Remove a directory and its contents:

rm -r directory_name

«⚠️ Be careful with "rm -r". It can recursively remove a directory and its contents.»

"truncate" — Change File Size

Creates an empty file or changes the size of an existing file.

truncate -s 0 file.txt

For example, the following creates or resizes a file to 100 MB:

truncate -s 100M file.img

---

🔐 Privilege Management

"sudo -i" — Start a Root Shell

Starts a root login shell using "sudo".

sudo -i

«Use root privileges only when necessary.»

---

🕘 Command History

"history"

Displays previously executed commands.

history

A specific command can be executed by its history number:

!300

This executes command number "300" from the current shell's history.

---

📖 Getting Help

"man" — Manual Pages

Displays the manual page for a command.

man ls

Another example:

man systemctl

Manual pages are an important built-in source of documentation in Linux.

"which" — Locate an Executable

Shows the executable that would be found through the current "PATH".

which python3

For example:

which ls

"whereis" — Locate Related Files

Searches for the binary, source, and manual pages associated with a command.

whereis ls

Another example:

whereis bash

---

🧠 Key Takeaways

- Linux administration heavily relies on the command line.
- Understanding paths and directory navigation is fundamental.
- "man" provides built-in documentation for many commands.
- "sudo" allows commands to be executed with elevated privileges.
- Commands such as "rm" should be used carefully.

---

🧪 Practice

These commands were studied and practiced as part of my Linux system administration learning.

Current focus: Building confidence with everyday command-line operations and understanding how Linux commands behave in practical environments.

---

Part of "My-Note" (../../../../README.md)

Personal technical knowledge base — continuously updated.
