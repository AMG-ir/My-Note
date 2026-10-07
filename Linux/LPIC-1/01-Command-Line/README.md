Linux Command Line

This section contains notes and practical examples related to basic Linux command-line usage.

Navigation

pwd

Displays the current working directory.

```bash
pwd
```

ls

Lists files and directories.

```bash
ls
ls -l
ls -la
```

cd

Changes the current working directory.

```bash
cd /path/to/directory
cd ..
cd ~
```

Files and Directories

mkdir

Creates a directory.

```bash
mkdir directory_name
mkdir -p parent/child
```

rmdir

Removes an empty directory.

```bash
rmdir directory_name
```

rm

Removes files or directories.

```bash
rm file.txt
rm -r directory_name
```

«Use "rm -r" carefully because it can remove directories and their contents.»

truncate

Creates an empty file or changes the size of an existing file.

```bash
truncate -s 0 file.txt
truncate -s 100M file.img
```

Privilege Management

sudo -i

Starts a root login shell.

```bash
sudo -i
```

Use elevated privileges only when necessary.

Command History

history

Displays previously executed commands.

```bash
history
```

A specific command can also be executed from the history:

```bash
!300
```

This executes command number "300" from the shell history.

Manual Pages

man

Displays the manual page for a command.

```bash
man ls
man systemctl
```

which

Shows the path of an executable found in the user's "PATH".

```bash
which python3
which ls
```

whereis

Locates the binary, source, and manual pages associated with a command.

```bash
whereis ls
whereis bash
```

Notes

· Most Linux administration tasks can be performed from the command line.
· Understanding command syntax and reading manual pages are important skills for system administration.
· Commands should be tested in a safe environment before being used on production systems.
