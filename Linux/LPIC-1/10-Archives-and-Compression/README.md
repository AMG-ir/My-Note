# 10 - Archives and Compression

This section covers creating, extracting, listing, and compressing archives using common Linux tools such as `tar`, `gzip`, `bzip2`, and `xz`.

## Overview

Archiving combines multiple files and directories into a single archive file. Compression reduces the size of data. They are related but different operations:

```text
Archiving
Multiple files/directories
        ↓
     One archive

Compression
Archive or file
        ↓
   Smaller size
```

The `tar` command is commonly used for archiving, while `gzip`, `bzip2`, and `xz` are used for compression.

## Contents

- [tar](#tar)
- [Gzip Compression](#gzip-compression)
- [Bzip2 Compression](#bzip2-compression)
- [XZ Compression](#xz-compression)
- [Direct Compression Commands](#direct-compression-commands)
- [Archive Format Comparison](#archive-format-comparison)
- [Common tar Options](#common-tar-options)
- [Practical Examples](#practical-examples)
- [Practice](#practice)
- [Key Takeaways](#key-takeaways)

---

## tar

`tar` is used to create and manage archives.

Basic syntax:

```bash
tar [options] archive files
```

A tar archive normally uses the `.tar` extension.

### Creating an Archive

Use `-c` to create an archive.

```bash
tar -cf archive.tar file1 file2
```

Example:

```bash
tar -cf backup.tar file1.txt file2.txt
```

To archive a directory:

```bash
tar -cf backup.tar mydirectory/
```

### Listing Archive Contents

Use `-t` to list the contents of an archive.

```bash
tar -tf archive.tar
```

Example:

```bash
tar -tf backup.tar
```

This displays the files and directories stored inside the archive.

### Extracting an Archive

Use `-x` to extract an archive.

```bash
tar -xf archive.tar
```

Example:

```bash
tar -xf backup.tar
```

The archive contents are extracted into the current directory.

### Extracting to a Specific Directory

The `-C` option can be used to specify the extraction directory.

```bash
tar -xf archive.tar -C /path/to/directory
```

Example:

```bash
tar -xf backup.tar -C /tmp
```

---

## Gzip Compression

`gzip` is a compression tool commonly used together with `tar`. A gzip-compressed tar archive normally uses `.tar.gz` or `.tgz`.

### Creating a .tar.gz Archive

```bash
tar -czf archive.tar.gz directory/
```

The options mean:

| Option | Meaning |
|--------|---------|
| `c`    | Create |
| `z`    | Use gzip compression |
| `f`    | Specify the archive file |

Example:

```bash
tar -czf backup.tar.gz mydirectory/
```

### Listing a .tar.gz Archive

```bash
tar -tzf archive.tar.gz
```

### Extracting a .tar.gz Archive

```bash
tar -xzf archive.tar.gz
```

Example:

```bash
tar -xzf backup.tar.gz
```

---

## Bzip2 Compression

`bzip2` is another compression tool. A tar archive compressed with bzip2 normally uses `.tar.bz2`.

### Creating a .tar.bz2 Archive

```bash
tar -cjf archive.tar.bz2 directory/
```

The `j` option tells `tar` to use bzip2 compression.

Example:

```bash
tar -cjf backup.tar.bz2 mydirectory/
```

### Listing a .tar.bz2 Archive

```bash
tar -tjf archive.tar.bz2
```

### Extracting a .tar.bz2 Archive

```bash
tar -xjf archive.tar.bz2
```

Example:

```bash
tar -xjf backup.tar.bz2
```

---

## XZ Compression

`xz` is another compression method commonly used with `tar`. A tar archive compressed with xz normally uses `.tar.xz`.

### Creating a .tar.xz Archive

```bash
tar -cJf archive.tar.xz directory/
```

The `J` option tells `tar` to use xz compression.

Example:

```bash
tar -cJf backup.tar.xz mydirectory/
```

### Listing a .tar.xz Archive

```bash
tar -tJf archive.tar.xz
```

### Extracting a .tar.xz Archive

```bash
tar -xJf archive.tar.xz
```

Example:

```bash
tar -xJf backup.tar.xz
```

---

## Direct Compression Commands

The compression tools can also be used directly on individual files.

### gzip

Compress a file:

```bash
gzip file.txt
```

This normally creates `file.txt.gz`. Decompress it with:

```bash
gzip -d file.txt.gz
```

### bzip2

Compress a file:

```bash
bzip2 file.txt
```

This normally creates `file.txt.bz2`. Decompress it with:

```bash
bzip2 -d file.txt.bz2
```

### xz

Compress a file:

```bash
xz file.txt
```

This normally creates `file.txt.xz`. Decompress it with:

```bash
xz -d file.txt.xz
```

---

## Archive Format Comparison

| Format       | Compression | Common Extension |
|--------------|-------------|------------------|
| TAR          | None        | `.tar`           |
| TAR + Gzip   | Gzip        | `.tar.gz`        |
| TAR + Bzip2  | Bzip2       | `.tar.bz2`       |
| TAR + XZ     | XZ          | `.tar.xz`        |

---

## Common tar Options

| Option | Purpose |
|--------|---------|
| `-c`   | Create an archive |
| `-x`   | Extract an archive |
| `-t`   | List archive contents |
| `-f`   | Specify the archive file |
| `-z`   | Use gzip compression |
| `-j`   | Use bzip2 compression |
| `-J`   | Use xz compression |
| `-C`   | Change directory for extraction |

---

## Practical Examples

### Create a TAR Archive

```bash
tar -cf backup.tar mydirectory/
```

### List a TAR Archive

```bash
tar -tf backup.tar
```

### Extract a TAR Archive

```bash
tar -xf backup.tar
```

### Create a Gzip Archive

```bash
tar -czf backup.tar.gz mydirectory/
```

### List a Gzip Archive

```bash
tar -tzf backup.tar.gz
```

### Extract a Gzip Archive

```bash
tar -xzf backup.tar.gz
```

### Create a Bzip2 Archive

```bash
tar -cjf backup.tar.bz2 mydirectory/
```

### List a Bzip2 Archive

```bash
tar -tjf backup.tar.bz2
```

### Extract a Bzip2 Archive

```bash
tar -xjf backup.tar.bz2
```

### Create an XZ Archive

```bash
tar -cJf backup.tar.xz mydirectory/
```

### List an XZ Archive

```bash
tar -tJf backup.tar.xz
```

### Extract an XZ Archive

```bash
tar -xJf backup.tar.xz
```

---

## Practice

### Create a Test Directory

```bash
mkdir archive-test
```

### Create Test Files

```bash
touch archive-test/file1.txt archive-test/file2.txt
```

### Create a TAR Archive

```bash
tar -cf archive.tar archive-test/
```

### List the Archive

```bash
tar -tf archive.tar
```

### Extract the Archive

```bash
tar -xf archive.tar
```

### Create a Gzip Archive

```bash
tar -czf archive.tar.gz archive-test/
```

### Create a Bzip2 Archive

```bash
tar -cjf archive.tar.bz2 archive-test/
```

### Create an XZ Archive

```bash
tar -cJf archive.tar.xz archive-test/
```

---

## Key Takeaways

- `tar` is used to create, list, and extract archives.
- Archiving and compression are different operations.
- `gzip`, `bzip2`, and `xz` provide different compression methods.
- `tar -czf` creates a gzip-compressed archive.
- `tar -cjf` creates a bzip2-compressed archive.
- `tar -cJf` creates an xz-compressed archive.
- `tar -xf` extracts an archive.
- `tar -tf` lists the contents of an archive.
- `gzip`, `bzip2`, and `xz` can also be used directly on individual files.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
