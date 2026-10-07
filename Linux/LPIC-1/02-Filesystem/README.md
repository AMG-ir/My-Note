Linux Filesystem

Notes on the Linux filesystem hierarchy, paths, files, directories, and filesystem-related concepts.

---

Overview

The Linux filesystem is organized as a hierarchical tree.

Unlike Windows, Linux uses a single directory tree that starts at the root directory /.

Understanding the filesystem hierarchy is essential for Linux system administration.

---

Filesystem Hierarchy

The main directories commonly found under / include:

Directory Purpose
/ Root of the entire filesystem
/home Home directories for regular users
/root Home directory of the root user
/etc System-wide configuration files
/var Variable data such as logs, caches, and application data
/tmp Temporary files
/usr User-space programs, libraries, and shared data
/opt Optional or third-party software
/dev Device files
/proc Virtual filesystem providing process and kernel information
/sys Virtual filesystem providing information about devices and the kernel
/boot Files required for the boot process

---

/ — Root Directory

The / directory is the starting point of the Linux filesystem hierarchy.

All other directories and mounted filesystems are located somewhere below /.

Example:

```bash
ls /
```

---

/home

/home contains the home directories of regular users.

For example:

```
/home/matin
/home/user1
/home/user2
```

A user's personal files are normally stored inside their home directory.

You can move to your home directory with:

```bash
cd ~
```

or:

```bash
cd $HOME
```

---

/root

/root is the home directory of the root user.

It is different from /, which is the root of the entire filesystem.

Example:

```bash
sudo -i
cd /root
```

---

/etc

/etc contains system-wide configuration files.

Examples include:

```
/etc/passwd
/etc/shadow
/etc/group
/etc/hosts
/etc/fstab
```

Configuration files in /etc are important when managing users, networking, storage, services, and other system components.

---

/var

/var contains data that is expected to change during normal system operation.

Common examples include:

```
/var/log
/var/cache
/var/lib
```

System and application logs are commonly stored under:

```
/var/log
```

Example:

```bash
ls /var/log
```

---

/tmp

/tmp is used for temporary files created by applications and users.

Example:

```bash
cd /tmp
```

Temporary files should generally not be used for permanent data storage.

---

/usr

/usr contains many user-space programs, libraries, and shared data.

Common directories include:

```
/usr/bin
/usr/sbin
/usr/lib
/usr/share
```

For example:

```bash
ls /usr/bin
```

---

/opt

/opt is commonly used for optional or third-party software.

Example:

```
/opt/application/
```

---

/dev

/dev contains device files used by the Linux system to interact with hardware and certain virtual devices.

Examples include:

```
/dev/sda
/dev/null
/dev/zero
```

You can inspect the directory with:

```bash
ls /dev
```

---

/proc

/proc is a virtual filesystem that provides information about processes and the running kernel.

It does not behave like a normal disk-based filesystem.

Examples:

```
/proc/cpuinfo
/proc/meminfo
/proc/version
```

Information can be viewed using commands such as:

```bash
cat /proc/cpuinfo
cat /proc/meminfo
cat /proc/version
```

Process-specific information can also be found under directories named by process ID (PID).

For example:

```
/proc/1
/proc/1000
```

---

/sys

/sys is another virtual filesystem that provides information about devices, hardware, and the Linux kernel.

It is commonly used to inspect and interact with kernel device information.

Example:

```bash
ls /sys
```

---

/boot

/boot contains files required during the system boot process.

Depending on the system, it may contain files such as:

```
vmlinuz
initramfs
grub/
```

---

Paths

Linux paths can be absolute or relative.

Absolute Path

An absolute path starts from /.

Example:

```
/etc/passwd
```

Another example:

```
/home/matin/Documents
```

An absolute path does not depend on the current working directory.

Relative Path

A relative path is interpreted from the current working directory.

For example, if the current directory is:

```
/home/matin
```

then:

```bash
cd Documents
```

refers to:

```
/home/matin/Documents
```

---

Special Path Components

Linux provides special directory references:

Symbol Meaning
. Current directory
.. Parent directory
~ Current user's home directory
/ Root directory

Examples:

```bash
cd .
cd ..
cd ~
cd /
```

---

Working with Files and Directories

pwd

Displays the current working directory.

```bash
pwd
```

ls

Lists directory contents.

```bash
ls
ls -l
ls -la
```

Useful options:

Option Description
-l Long listing format
-a Show hidden files
-h Human-readable file sizes

Example:

```bash
ls -lah
```

cd

Changes the current working directory.

```bash
cd /etc
cd ..
cd ~
```

mkdir

Creates directories.

```bash
mkdir test
```

Create nested directories:

```bash
mkdir -p project/src/config
```

rmdir

Removes an empty directory.

```bash
rmdir test
```

It does not remove directories that contain files.

rm

Removes files and directories.

Remove a file:

```bash
rm file.txt
```

Remove a directory and its contents:

```bash
rm -r directory
```

Be careful when using rm, especially with recursive operations.

touch

Creates an empty file or updates the timestamps of an existing file.

```bash
touch file.txt
```

file

Determines the type of a file based on its contents.

```bash
file file.txt
```

Example:

```bash
file /bin/bash
```

---

Hidden Files

In Linux, files and directories whose names begin with . are normally treated as hidden.

Example:

```
.bashrc
.profile
.config
```

They can be displayed using:

```bash
ls -la
```

---

File and Directory Information

du

Displays disk usage.

Example:

```bash
du -h
```

To display the total size of a directory:

```bash
du -sh directory/
```

df

Displays filesystem disk space usage.

```bash
df -h
```

Unlike du, which examines files and directories, df reports filesystem-level space usage.

---

Finding Files

find

Searches for files and directories.

Search by name:

```bash
find /home -name "file.txt"
```

Search for directories:

```bash
find /home -type d -name "Documents"
```

Search for regular files:

```bash
find /home -type f -name "*.txt"
```

Common type options:

Option Meaning
-type f Regular file
-type d Directory
-type l Symbolic link

---

Symbolic Links

A symbolic link is a special file that points to another file or directory.

Create a symbolic link:

```bash
ln -s /path/to/original /path/to/link
```

Example:

```bash
ln -s /var/log/example.log ~/example.log
```

List the link:

```bash
ls -l ~/example.log
```

The output shows the target of the symbolic link.

---

Mount Points

Linux can attach filesystems to directories called mount points.

For example, a filesystem can be mounted at:

```
/mnt
```

or:

```
/media
```

The mount command can be used to view mounted filesystems:

```bash
mount
```

A more readable overview can be obtained with:

```bash
findmnt
```

---

/etc/fstab

The /etc/fstab file contains information about filesystems that can be mounted automatically during system startup.

View the file with:

```bash
cat /etc/fstab
```

A typical entry contains information such as:

```
UUID=<filesystem-uuid>  /mount/point  ext4  defaults  0  2
```

Changes to /etc/fstab should be made carefully because incorrect entries can cause boot or mounting problems.

---

Device Names

Linux commonly represents storage devices under /dev.

Examples include:

```
/dev/sda
/dev/sdb
```

Partitions may appear as:

```
/dev/sda1
/dev/sda2
```

On systems using NVMe storage, device names may look like:

```
/dev/nvme0n1
/dev/nvme0n1p1
```

The exact device names depend on the hardware and storage configuration.

---

Useful Commands

The following commands are useful when inspecting the filesystem:

Command Purpose
pwd Show current directory
ls List directory contents
cd Change directory
mkdir Create directory
rmdir Remove empty directory
rm Remove files/directories
touch Create or update a file
file Identify file type
find Search for files/directories
du Show directory/file disk usage
df Show filesystem disk usage
mount Show or manage mounted filesystems
findmnt Display mounted filesystems
ln Create links

---

Key Takeaways

· Linux uses a single hierarchical filesystem starting at /.
· /etc contains system configuration files.
· /var contains changing system and application data.
· /dev, /proc, and /sys provide interfaces to devices, processes, and kernel information.
· Absolute paths start from /, while relative paths depend on the current working directory.
· Hidden files usually begin with ..
· find can be used to search for files and directories.
· df reports filesystem space usage, while du reports file and directory usage.
· Filesystems can be attached to the directory tree using mount points.
· /etc/fstab can be used to define filesystem mount configuration.

---

Practice

These topics were studied as part of my Linux system administration learning.

The goal is to understand the Linux filesystem hierarchy and become comfortable navigating, inspecting, and managing files and directories from the command line.

---

Part of My-Note
Personal technical knowledge base — continuously updated.
