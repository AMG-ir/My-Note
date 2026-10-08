# 05 - Permissions

This section covers Linux file and directory permissions, ownership, permission modes, and the commands used to manage them.

## Overview

Linux uses permissions to control access to files and directories.

Permissions are applied to three categories:

- User (owner)
- Group
- Others

The three basic permissions are:

- `r`: Read
- `w`: Write
- `x`: Execute

## Contents

- [Viewing Permissions](#viewing-permissions)
- [Permission Types](#permission-types)
- [Permission Groups](#permission-groups)
- [chmod](#chmod)
- [Symbolic Permissions](#symbolic-permissions)
- [Numeric Permissions](#numeric-permissions)
- [chown](#chown)
- [umask](#umask)
- [Checking Permissions](#checking-permissions)
- [Practical Examples](#practical-examples)
- [Common Permission Modes](#common-permission-modes)
- [Useful Commands](#useful-commands)
- [Practice](#practice)
- [Key Takeaways](#key-takeaways)

---

## Viewing Permissions

The `ls -l` command can be used to view file and directory permissions.

```bash
ls -l
```

Example output:

```text
-rw-r--r-- 1 user user 1234 file.txt
```

The first part represents the permissions:

```text
-rw-r--r--
```

The permissions are divided into four parts:

```text
- rw- r-- r--
  │   │   │
  │   │   └── Others
  │   └────── Group
  └────────── Owner
```

The first character represents the file type:

```text
-    regular file
d    directory
```

---

## Permission Types

| Permission | Symbol | Meaning |
|------------|--------|---------|
| Read       | `r`    | Allows reading the contents of a file |
| Write      | `w`    | Allows modifying a file |
| Execute    | `x`    | Allows executing a file |

For directories, permissions affect access to the directory itself and its contents.

---

## Permission Groups

Each file has permissions for three categories:

| Category | Description |
|----------|-------------|
| Owner    | The user who owns the file |
| Group    | The group associated with the file |
| Others   | All other users |

Example:

```text
-rwxr-xr--
```

This means:

```text
Owner   rwx
Group   r-x
Others  r--
```

Breaking the string into parts:

```text
- rwx r-x r--
  │   │   │
  │   │   └── Others
  │   └────── Group
  └────────── Owner
```

Therefore:

- Owner: read, write, execute
- Group: read, execute
- Others: read

---

## chmod

`chmod` is used to change file and directory permissions.

Basic syntax:

```bash
chmod [permissions] file
```

Example:

```bash
chmod u+x script.sh
```

This adds execute permission for the owner.

---

## Symbolic Permissions

Permissions can be changed using symbolic notation.

| Symbol | Meaning |
|--------|---------|
| `u`    | User / owner |
| `g`    | Group |
| `o`    | Others |
| `a`    | All |

| Operator | Meaning |
|----------|---------|
| `+`      | Add permission |
| `-`      | Remove permission |
| `=`      | Set permission |

### Add Execute Permission for Owner

```bash
chmod u+x file
```

### Remove Write Permission from Group

```bash
chmod g-w file
```

### Add Read Permission for Others

```bash
chmod o+r file
```

### Set Permissions for Owner

```bash
chmod u=rwx file
```

---

## Numeric Permissions

Permissions can also be represented using numbers.

| Permission | Value |
|------------|-------|
| Read (`r`)    | 4 |
| Write (`w`)   | 2 |
| Execute (`x`) | 1 |

The values are added together for each permission group.

```text
r-- = 4
-w- = 2
--x = 1
rw- = 6
r-x = 5
-wx = 3
rwx = 7
```

For example:

```bash
chmod 755 file
```

represents:

```text
Owner   7 = rwx
Group   5 = r-x
Others  5 = r-x
```

Another example:

```bash
chmod 644 file
```

represents:

```text
Owner   6 = rw-
Group   4 = r--
Others  4 = r--
```

---

## chown

`chown` is used to change the owner of a file or directory.

Basic syntax:

```bash
sudo chown user file
```

Example:

```bash
sudo chown username file.txt
```

The owner of `file.txt` is changed to `username`.

### Changing Owner and Group

`chown` can also be used to change both the owner and the group.

```bash
sudo chown username:groupname file.txt
```

Example:

```bash
sudo chown matin:developers file.txt
```

---

## umask

`umask` controls the default permission mask used when new files and directories are created.

Display the current umask:

```bash
umask
```

Example output:

```text
0022
```

The value affects the default permissions assigned to newly created files and directories.

---

## Checking Permissions

Use `ls -l` to inspect permissions and ownership:

```bash
ls -l
```

Example output:

```text
-rw-r--r-- 1 username groupname 1200 file.txt
```

This output provides information about:

- File type
- Permissions
- Owner
- Group
- File size
- File name

---

## Practical Examples

### Check File Permissions

```bash
ls -l file.txt
```

### Add Execute Permission

```bash
chmod u+x file.txt
```

### Remove Write Permission

```bash
chmod u-w file.txt
```

### Set Permissions to 755

```bash
chmod 755 file.txt
```

### Set Permissions to 644

```bash
chmod 644 file.txt
```

### Change File Owner

```bash
sudo chown username file.txt
```

### Change Owner and Group

```bash
sudo chown username:groupname file.txt
```

### Check Current umask

```bash
umask
```

---

## Common Permission Modes

| Mode  | Owner | Group | Others |
|-------|-------|-------|--------|
| `777` | `rwx` | `rwx` | `rwx`  |
| `755` | `rwx` | `r-x` | `r-x`  |
| `700` | `rwx` | `---` | `---`  |
| `666` | `rw-` | `rw-` | `rw-`  |
| `644` | `rw-` | `r--` | `r--`  |
| `600` | `rw-` | `---` | `---`  |

---

## Useful Commands

| Command    | Purpose |
|------------|---------|
| `ls -l`    | View permissions and ownership |
| `chmod`    | Change permissions |
| `chown`    | Change file ownership |
| `umask`    | View the default permission mask |

---

## Practice

### Create a Test File

```bash
touch permissions-test.txt
```

### View Its Permissions

```bash
ls -l permissions-test.txt
```

### Change Its Permissions

```bash
chmod 600 permissions-test.txt
```

### Check the Result

```bash
ls -l permissions-test.txt
```

### Change Permissions Symbolically

```bash
chmod u+x permissions-test.txt
```

### Check the Result Again

```bash
ls -l permissions-test.txt
```

### Check the Current umask

```bash
umask
```

---

## Key Takeaways

- Linux permissions control access to files and directories.
- Permissions are divided between the owner, group, and others.
- The basic permissions are read, write, and execute.
- `ls -l` can be used to view permissions and ownership.
- `chmod` changes file and directory permissions.
- Permissions can be specified symbolically or numerically.
- `chown` changes file ownership.
- `umask` affects the default permissions of newly created files and directories.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
