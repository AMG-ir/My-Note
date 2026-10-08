# 11 - Shell Tools

This section covers basic Linux shell tools used to search, filter, process, and manipulate text and command output.

## Overview

Linux provides several command-line tools for working with text and command output.

The main tools covered in this section are:

- `grep`
- `sed`
- `head`
- `tail`
- `wc`
- `xargs`
- Pipes
- Output redirection

## Contents

- [Pipes](#pipes)
- [Output Redirection](#output-redirection)
- [grep](#grep)
- [sed](#sed)
- [head](#head)
- [tail](#tail)
- [wc](#wc)
- [xargs](#xargs)
- [Combining Shell Tools](#combining-shell-tools)
- [Practical Examples](#practical-examples)
- [Useful Commands](#useful-commands)
- [Key Takeaways](#key-takeaways)

---

## Pipes

A pipe (`|`) sends the output of one command to another command as input.

Basic syntax:

```bash
command1 | command2
```

Example:

```bash
ls | grep ".txt"
```

In this example, the output of `ls` is passed to `grep`.

Pipes can also be chained:

```bash
command1 | command2 | command3
```

---

## Output Redirection

Redirection is used to send command output to a file or to provide input from a file.

### `>`

Writes command output to a file.

```bash
command > file.txt
```

Example:

```bash
ls > files.txt
```

> **Note:** If the file already exists, its contents are replaced.

### `>>`

Appends command output to a file.

```bash
command >> file.txt
```

Example:

```bash
echo "New line" >> notes.txt
```

Existing content is preserved and the new output is added to the end.

### `<`

Provides a file as input to a command.

```bash
command < file.txt
```

---

## grep

Searches for matching text.

Basic syntax:

```bash
grep "pattern" file
```

Example:

```bash
grep "error" log.txt
```

This searches `log.txt` for lines containing `error`.

### Case-Insensitive Search

The `-i` option makes the search case-insensitive.

```bash
grep -i "error" log.txt
```

This can match:

```text
error
Error
ERROR
```

### Searching Command Output

`grep` can be combined with a pipe.

```bash
ps | grep ssh
```

The output of `ps` is passed to `grep`, which filters the results.

Another example:

```bash
ls | grep ".conf"
```

---

## sed

`sed` is a stream editor used to process and modify text.

Basic syntax:

```bash
sed 'command' file
```

A common operation is replacing text:

```bash
sed 's/old/new/' file.txt
```

This replaces the first occurrence of `old` with `new` on each processed line.

### Global Replacement

The `g` flag replaces all matching occurrences on each line.

```bash
sed 's/old/new/g' file.txt
```

### Editing a File In Place

The `-i` option modifies the file directly.

```bash
sed -i 's/old/new/g' file.txt
```

> **Warning:** The original file is modified in place.

---

## head

Displays the beginning of a file or command output. By default, it displays the first part of the input.

```bash
head file.txt
```

### Displaying a Specific Number of Lines

Use `-n` to specify the number of lines.

```bash
head -n 5 file.txt
```

This displays the first five lines.

---

## tail

Displays the end of a file or command output.

```bash
tail file.txt
```

### Displaying a Specific Number of Lines

```bash
tail -n 5 file.txt
```

This displays the last five lines.

### Following a File

`tail -f` continuously displays new content added to a file. This is useful when monitoring log files.

```bash
tail -f log.txt
```

---

## wc

Counts lines, words, and bytes.

```bash
wc file.txt
```

The output includes:

```text
lines words bytes
```

| Option | Purpose |
|--------|---------|
| `-l`   | Count lines |
| `-w`   | Count words |
| `-c`   | Count bytes |

```bash
wc -l file.txt
wc -w file.txt
wc -c file.txt
```

### Combining wc with Pipes

```bash
ls | wc -l
```

This counts the number of lines in the output of `ls`.

---

## xargs

Builds and executes commands using input received from another command.

Basic syntax:

```bash
command | xargs command
```

Example:

```bash
echo "file1 file2 file3" | xargs rm
```

The input is passed as arguments to `rm`.

### Using xargs with grep

```bash
find . -type f | xargs grep "error"
```

This passes the resulting file names to `grep`.

---

## Combining Shell Tools

Shell tools become more useful when combined with pipes.

```bash
ps | grep ssh
```

Another example:

```bash
cat log.txt | grep error | wc -l
```

This:

1. Reads the file.
2. Filters lines containing `error`.
3. Counts the resulting lines.

---

## Practical Examples

### Search a File

```bash
grep "error" log.txt
```

### Case-Insensitive Search

```bash
grep -i "error" log.txt
```

### Search Command Output

```bash
ps | grep ssh
```

### Display the First Five Lines

```bash
head -n 5 file.txt
```

### Display the Last Five Lines

```bash
tail -n 5 file.txt
```

### Monitor a Log File

```bash
tail -f log.txt
```

### Count Lines

```bash
wc -l file.txt
```

### Replace Text

```bash
sed 's/old/new/g' file.txt
```

### Modify a File Directly

```bash
sed -i 's/old/new/g' file.txt
```

### Save Command Output

```bash
ls > files.txt
```

### Append Command Output

```bash
ls >> files.txt
```

### Count Filtered Results

```bash
ps | grep ssh | wc -l
```

---

## Useful Commands

| Command   | Purpose |
|-----------|---------|
| `grep`    | Search and filter text |
| `sed`     | Process and modify text |
| `head`    | Display the beginning of input |
| `tail`    | Display the end of input |
| `tail -f` | Follow new content in a file |
| `wc`      | Count lines, words, and bytes |
| `xargs`   | Build commands from input |
| `\|`      | Pass output of one command to another |
| `>`       | Write output to a file |
| `>>`      | Append output to a file |
| `<`       | Provide file input to a command |

---

## Key Takeaways

- Pipes connect commands together.
- Redirection can send command output to files.
- `grep` searches and filters text.
- `sed` processes and modifies text.
- `head` displays the beginning of input.
- `tail` displays the end of input.
- `tail -f` can monitor new log entries.
- `wc` counts lines, words, and bytes.
- `xargs` uses input to build command arguments.
- Combining shell tools makes command-line operations more powerful.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
