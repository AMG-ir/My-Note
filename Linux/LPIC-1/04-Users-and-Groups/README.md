Users and Groups

This section covers Linux user and group management, including user information, account files, creating and modifying users and groups, and managing passwords.

Overview

Linux is a multi-user operating system. Users and groups are used to manage accounts and organize access to system resources.

User and group information is stored in specific files under /etc.

---

User Information

id

Displays information about the current user or a specified user.

```bash
id
```

Example:

```bash
id username
```

The output includes information such as:

· User ID (UID)
· Group ID (GID)
· Groups the user belongs to

---

groups

Displays the groups that a user belongs to.

```bash
groups
```

Example:

```bash
groups username
```

---

Important Account Files

Linux stores user and group information in several files.

/etc/passwd

Contains information about local user accounts.

```bash
cat /etc/passwd
```

A typical entry contains fields such as:

```
username:x:UID:GID:comment:home_directory:login_shell
```

The fields are separated by :.

---

/etc/group

Contains information about groups on the system.

```bash
cat /etc/group
```

A typical entry contains:

```
groupname:x:GID:members
```

---

/etc/shadow

Stores password-related information for local user accounts.

```bash
sudo cat /etc/shadow
```

This file contains sensitive account information and normally requires elevated privileges to read.

---

Creating Users

adduser

Creates a new user account.

```bash
sudo adduser username
```

adduser provides an interactive process for creating the account and setting basic user information.

---

useradd

Creates a user account.

```bash
sudo useradd username
```

Unlike adduser, useradd is a lower-level command and is commonly used with additional options when creating accounts.

---

Modifying Users

usermod

Used to modify an existing user account.

```bash
sudo usermod [options] username
```

The command can be used to change properties of an existing user account.

Example:

```bash
sudo usermod -aG groupname username
```

This adds the user to an additional group.

---

Groups

Groups provide a way to organize users.

A user can belong to one or more groups.

groupadd

Creates a new group.

```bash
sudo groupadd groupname
```

---

groupdel

Deletes an existing group.

```bash
sudo groupdel groupname
```

---

Password Management

passwd

Used to set or change a user's password.

For the current user:

```bash
passwd
```

For another user:

```bash
sudo passwd username
```

---

Useful Commands

Command Purpose
id Display user and group information
groups Display a user's groups
adduser Create a user interactively
useradd Create a user
usermod Modify a user
groupadd Create a group
groupdel Delete a group
passwd Set or change a password

---

Important Files

File Purpose
/etc/passwd User account information
/etc/group Group information
/etc/shadow Password-related account information

---

Practice

The following exercises can be used to practice the concepts covered in this section.

Check Current User Information

```bash
id
```

Check Group Membership

```bash
groups
```

Create a User

```bash
sudo adduser testuser
```

Check the User

```bash
id testuser
```

Create a Group

```bash
sudo groupadd testgroup
```

Add the User to the Group

```bash
sudo usermod -aG testgroup testuser
```

Check Group Membership Again

```bash
groups testuser
```

Change the User Password

```bash
sudo passwd testuser
```

Remove the Test Group

```bash
sudo groupdel testgroup
```

---

Key Takeaways

· Linux supports multiple users and groups.
· id and groups can be used to inspect user and group membership.
· /etc/passwd, /etc/group, and /etc/shadow contain important account information.
· adduser and useradd can be used to create users.
· usermod is used to modify existing users.
· groupadd and groupdel manage groups.
· passwd is used to manage user passwords.
