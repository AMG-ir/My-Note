# 03 - Processes

Notes on Linux processes, process monitoring, signals, job control, and process priority.

## Overview

A process is a running instance of a program. Linux provides several commands for viewing, monitoring, controlling, and managing processes.

This section covers the process-related commands and concepts studied during my Linux system administration learning.

## Contents

- [Process Identification](#process-identification)
- [Viewing and Monitoring Processes](#viewing-and-monitoring-processes)
- [Finding Processes](#finding-processes)
- [Process States](#process-states)
- [Signals](#signals)
- [Job Control](#job-control)
- [Background Processes](#background-processes)
- [Process Priority](#process-priority)
- [Useful Commands](#useful-commands)
- [Practical Examples](#practical-examples)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## Process Identification

Every running process has a unique Process ID (PID). The PID can be used to identify and manage a specific process.

---

## Viewing and Monitoring Processes

### ps

Displays information about running processes.

```bash
ps
```

A more detailed view of processes can be displayed with:

```bash
ps aux
```

Another common format is:

```bash
ps -ef
```

The output can be used to inspect information such as:

- PID
- Process owner
- CPU usage
- Memory usage
- Process state
- Command

### pstree

Displays running processes in a tree structure.

```bash
pstree
```

This shows the relationship between parent and child processes and makes it easier to understand how processes are started by other processes.

### top

Provides a real-time view of running processes and system activity.

```bash
top
```

It can be used to monitor:

- CPU usage
- Memory usage
- Running processes
- Process IDs
- Process priorities

Press `q` to exit `top`.

### htop

Provides an interactive, more user-friendly view of running processes. Processes can be inspected and managed directly from the interface.

```bash
htop
```

Press `q` to exit `htop`.

---

## Finding Processes

### pgrep

Searches for processes based on their name or other criteria and returns the PIDs of matching processes.

```bash
pgrep bash
```

### pidof

Returns the PIDs associated with a specified program.

```bash
pidof bash
```

---

## Process States

A process can have different states during its lifecycle.

| State | Meaning |
|-------|---------|
| `R`   | Running or runnable |
| `S`   | Interruptible sleep |
| `D`   | Uninterruptible sleep |
| `T`   | Stopped |
| `Z`   | Zombie |

Process states can be observed using tools such as `ps` and `top`.

---

## Signals

Signals are used to send notifications or requests to processes. A process can receive different signals depending on the action being performed.

| Signal    | Number | Purpose |
|-----------|--------|---------|
| `SIGTERM` | 15     | Requests graceful termination |
| `SIGKILL` | 9      | Forces process termination |
| `SIGSTOP` | 19     | Stops a process |
| `SIGCONT` | 18     | Continues a stopped process |

### kill

Sends a signal to a process using its PID.

```bash
kill 1234
```

By default, `kill` sends `SIGTERM`. A specific signal can be specified:

```bash
kill -TERM 1234
```

To forcefully terminate a process:

```bash
kill -KILL 1234
```

or:

```bash
kill -9 1234
```

> **Warning:** Use `SIGKILL` carefully because the process cannot handle or ignore it.

---

## Job Control

Linux shells provide job control for managing processes started from the current shell.

### Ctrl+C

Sends an interrupt signal to the foreground process. It is commonly used to stop a running command.

```bash
ping example.com
```

Press `Ctrl+C` to interrupt the command.

### Ctrl+Z

Suspends the currently running foreground process.

```bash
ping example.com
```

Press `Ctrl+Z`. The process is stopped and becomes a shell job.

### jobs

Displays jobs managed by the current shell.

```bash
jobs
```

The output may show a stopped or background job.

### fg

Brings a background or stopped job to the foreground.

```bash
fg
```

A specific job can be selected by its job number:

```bash
fg %1
```

### bg

Resumes a stopped job in the background.

```bash
bg
```

A specific job can be selected:

```bash
bg %1
```

---

## Background Processes

A command can be started directly in the background by adding `&` to the end.

```bash
sleep 100 &
```

The shell returns control to the user while the command continues running in the background. The running job can be viewed with:

```bash
jobs
```

---

## Process Priority

Linux processes have a priority value that affects how the scheduler handles CPU time. The nice value is used to influence process priority.

### renice

Changes the nice value of an already running process.

```bash
renice 10 -p 1234
```

The command above changes the nice value of process 1234. A process's priority information can be inspected using `ps` or `top`.

> **Note:** Process priority should be changed carefully because it can affect CPU scheduling.

---

## Useful Commands

| Command  | Purpose |
|----------|---------|
| `ps`     | Display process information |
| `pstree` | Display processes as a tree |
| `top`    | Monitor processes in real time |
| `htop`   | Interactive process monitoring |
| `pgrep`  | Find processes by name or criteria |
| `pidof`  | Find PIDs associated with a program |
| `kill`   | Send a signal to a process |
| `jobs`   | Display shell jobs |
| `fg`     | Bring a job to the foreground |
| `bg`     | Resume a job in the background |
| `renice` | Change the nice value of a running process |

---

## Practical Examples

### Find a Process

```bash
pgrep bash
```

### Inspect Processes

```bash
ps aux
```

### Monitor Processes

```bash
top
```

or:

```bash
htop
```

### Stop a Foreground Process

Run a command such as:

```bash
ping example.com
```

Then press `Ctrl+C`.

### Suspend and Resume a Process

Start a command:

```bash
ping example.com
```

Press `Ctrl+Z`, then check the job:

```bash
jobs
```

Resume it in the background:

```bash
bg
```

Bring it back to the foreground:

```bash
fg
```

### Terminate a Process

Find the PID:

```bash
pgrep process_name
```

Then send a termination signal:

```bash
kill PID
```

---

## Key Takeaways

- Every running process has a PID.
- `ps`, `top`, and `htop` can be used to inspect running processes.
- `pstree` shows parent-child process relationships.
- `pgrep` and `pidof` can be used to find process IDs.
- Signals provide a way to communicate with or control processes.
- `kill` can send signals to processes.
- `Ctrl+C` interrupts a foreground process.
- `Ctrl+Z` suspends a foreground process.
- `jobs`, `fg`, and `bg` provide shell job control.
- `renice` can change the nice value of a running process.

## Practice

These commands and concepts were studied as part of my Linux system administration learning.

The goal is to become comfortable with inspecting processes, understanding process states, controlling shell jobs, working with signals, and managing process priority.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
