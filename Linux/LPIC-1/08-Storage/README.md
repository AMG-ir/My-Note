Storage

This section covers Linux storage management, including disks, partitions, filesystems, mounting, /etc/fstab, and basic LVM operations.

Overview

Linux storage management involves several layers:

```text
Disk
  ↓
Partition
  ↓
Filesystem
  ↓
Mount Point
```

LVM provides another layer that allows storage to be managed using physical volumes, volume groups, and logical volumes.

---

Block Devices

Linux represents disks and partitions as block devices.

Common device names include:

```
/dev/sda
/dev/sdb
/dev/sda1
/dev/sda2
```

For example:

```
/dev/sda
```

can represent a disk, while:

```
/dev/sda1
```

can represent a partition on that disk.

---

lsblk

lsblk displays information about block devices.

```bash
lsblk
```

It can show:

· Disk devices
· Partitions
· Device relationships
· Mount points

A more detailed view can be displayed with:

```bash
lsblk -f
```

---

fdisk

fdisk is used to manage disk partitions.

To work with a disk:

```bash
sudo fdisk /dev/sda
```

Inside fdisk, available options can be displayed with:

```
m
```

Common operations include viewing and modifying partition information.

---

parted

parted is another tool used for partition management.

Example:

```bash
sudo parted /dev/sda
```

It can be used to inspect and manage disk partitions.

---

Filesystems

A filesystem provides a structure for storing and accessing files on a storage device.

One filesystem used in Linux is ext4.

---

mkfs.ext4

mkfs.ext4 creates an ext4 filesystem on a device.

Example:

```bash
sudo mkfs.ext4 /dev/sdb1
```

This creates an ext4 filesystem on /dev/sdb1.

Formatting a device destroys the existing filesystem data on that device.

---

Mounting Filesystems

A filesystem must be mounted before it can normally be accessed through a directory.

mount

The mount command is used to mount filesystems.

Basic syntax:

```bash
sudo mount device mount-point
```

Example:

```bash
sudo mount /dev/sdb1 /mnt
```

The filesystem on /dev/sdb1 is mounted at /mnt.

---

Mount Points

A mount point is a directory where a filesystem becomes accessible.

For example:

```
/dev/sdb1
    |
    v
  /mnt
```

After mounting:

```bash
ls /mnt
```

can be used to access the mounted filesystem.

---

Viewing Mounted Filesystems

The mount command without arguments can display currently mounted filesystems.

```bash
mount
```

lsblk can also display mount point information:

```bash
lsblk
```

---

Unmounting Filesystems

umount

The umount command is used to unmount a filesystem.

Using the device:

```bash
sudo umount /dev/sdb1
```

Or using the mount point:

```bash
sudo umount /mnt
```

A filesystem should be unmounted before removing or disconnecting the associated storage device.

---

/etc/fstab

/etc/fstab contains filesystem mount configuration.

The file can be viewed with:

```bash
cat /etc/fstab
```

It can also be edited with a text editor.

A typical entry contains information such as:

```
device   mount-point   filesystem   options   dump   pass
```

For example:

```
/dev/sdb1 /mnt ext4 defaults 0 2
```

The purpose of /etc/fstab is to define filesystems that should be mounted according to the system configuration.

---

Testing /etc/fstab

After modifying /etc/fstab, the configuration can be tested by mounting filesystems defined in the file:

```bash
sudo mount -a
```

This attempts to mount the filesystems configured in /etc/fstab.

---

LVM

Overview

LVM (Logical Volume Manager) provides a flexible way to manage storage.

The basic LVM structure is:

```
Physical Volume (PV)
        |
        v
Volume Group (VG)
        |
        v
Logical Volume (LV)
```

Physical Volume

A physical volume is a storage device or partition prepared for LVM.

Volume Group

A volume group is a storage pool created from one or more physical volumes.

Logical Volume

A logical volume is created from available space in a volume group and can be used similarly to a normal block device.

---

Creating a Physical Volume

pvcreate

pvcreate initializes a device for use with LVM.

Example:

```bash
sudo pvcreate /dev/sdb1
```

After this operation, /dev/sdb1 can be used as an LVM physical volume.

---

Creating a Volume Group

vgcreate

vgcreate creates a volume group from physical volumes.

Example:

```bash
sudo vgcreate vgdata /dev/sdb1
```

This creates a volume group named vgdata.

---

Creating a Logical Volume

lvcreate

lvcreate creates a logical volume inside a volume group.

Example:

```bash
sudo lvcreate -L 5G -n lvdata vgdata
```

This creates a logical volume named lvdata with a size of 5 GB inside vgdata.

The resulting logical volume can be referenced as:

```
/dev/vgdata/lvdata
```

---

Creating a Filesystem on an LVM Logical Volume

After creating a logical volume, a filesystem can be created on it.

Example:

```bash
sudo mkfs.ext4 /dev/vgdata/lvdata
```

The logical volume can then be mounted:

```bash
sudo mount /dev/vgdata/lvdata /mnt
```

---

lvdisplay

lvdisplay displays information about logical volumes.

```bash
sudo lvdisplay
```

It can show information about the logical volumes configured on the system.

---

lvremove

lvremove removes a logical volume.

Example:

```bash
sudo lvremove /dev/vgdata/lvdata
```

The command asks for confirmation before removing the logical volume.

Removing a logical volume can result in loss of the data stored on it.

---

LVM Example

A basic LVM workflow can look like this:

1. Create a Physical Volume

```bash
sudo pvcreate /dev/sdb1
```

2. Create a Volume Group

```bash
sudo vgcreate vgdata /dev/sdb1
```

3. Create a Logical Volume

```bash
sudo lvcreate -L 5G -n lvdata vgdata
```

4. Create an ext4 Filesystem

```bash
sudo mkfs.ext4 /dev/vgdata/lvdata
```

5. Create a Mount Point

```bash
sudo mkdir /mnt/lvdata
```

6. Mount the Logical Volume

```bash
sudo mount /dev/vgdata/lvdata /mnt/lvdata
```

7. Check the Storage

```bash
lsblk
```

---

Storage Troubleshooting Workflow

A basic storage troubleshooting process can start with identifying the available devices.

1. List Block Devices

```bash
lsblk
```

2. Check Filesystems

```bash
lsblk -f
```

3. Check Mounts

```bash
mount
```

4. Check /etc/fstab

```bash
cat /etc/fstab
```

5. Test /etc/fstab

```bash
sudo mount -a
```

---

Useful Commands

Command Purpose
lsblk Display block devices and partitions
lsblk -f Display filesystems and mount information
fdisk Manage disk partitions
parted Manage disk partitions
mkfs.ext4 Create an ext4 filesystem
mount Mount a filesystem
umount Unmount a filesystem
pvcreate Create an LVM physical volume
vgcreate Create an LVM volume group
lvcreate Create an LVM logical volume
lvdisplay Display logical volume information
lvremove Remove a logical volume

---

Key Takeaways

· Linux represents storage devices as block devices.
· lsblk is useful for inspecting disks, partitions, and mount points.
· fdisk and parted are used for partition management.
· mkfs.ext4 creates an ext4 filesystem.
· mount makes a filesystem accessible through a mount point.
· umount removes a filesystem from its mount point.
· /etc/fstab contains persistent filesystem mount configuration.
· LVM organizes storage into physical volumes, volume groups, and logical volumes.
· pvcreate, vgcreate, and lvcreate are used to build an LVM storage structure.
· lvdisplay displays logical volume information.
· lvremove removes a logical volume.
