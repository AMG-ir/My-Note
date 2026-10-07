Linux Processes

Notes on Linux processes, process monitoring, signals, job control, and process priority.

---

Overview

A process is a running instance of a program.

Linux provides several commands for viewing, monitoring, controlling, and managing processes.

This section covers the process-related commands and concepts studied during my Linux system administration learning.

---

Process Identification

Every running process has a unique Process ID (PID).

The PID can be used to identify and manage a specific process.

---

ps — Process Status

The ps command displays information about running processes.

Basic usage:

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

· PID
· Process owner
· CPU usage
· Memory usage
· Process state
· Command

---

pstree — Process Tree

pstree displays running processes in a tree structure.

```bash
pstree
```

This can help show the relationship between parent and child processes.

A process tree makes it easier to understand how processes are started by other processes.

---

top — Real-Time Process Monitoring

top provides a real-time view of running processes and system activity.

```bash
top
```

It can be used to monitor:

· CPU usage
· Memory usage
· Running processes
· Process IDs
· Process priorities

Press q to exit top.

---

htop — Interactive Process Viewer

htop provides an interactive view of running processes.

```bash
htop
```

It provides a more user-friendly interface for monitoring processes.

Processes can be inspected and managed directly from the interface.

Press q to exit htop.

---

Finding Processes

pgrep

pgrep searches for processes based on their name or other criteria.

Example:

```bash
pgrep bash
```

This returns the PID of matching processes.

---

pidof

pidof returns the PIDs associated with a specified program.

Example:

```bash
pidof bash
```

---

Process States

A process can have different states during its lifecycle.

Common process states include:

State Meaning
R Running or runnable
S Interruptible sleep
D Uninterruptible sleep
T Stopped
Z Zombie

Process states can be observed using tools such as ps and top.

---

Signals

Signals are used to send notifications or requests to processes.

A process can receive different signals depending on the action being performed.

Some commonly used signals include:

Signal Number Purpose
SIGTERM 15 Requests graceful termination
SIGKILL 9 Forces process termination
SIGSTOP 19 Stops a process
SIGCONT 18 Continues a stopped process

---

kill — Send a Signal to a Process

The kill command can be used to send a signal to a process using its PID.

Example:

```bash
kill 1234
```

By default, kill sends SIGTERM.

A specific signal can be specified:

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

SIGKILL should be used carefully because the process cannot handle or ignore it.

---

Job Control

Linux shells provide job control for managing processes started from the current shell.

---

Ctrl+C

Ctrl+C sends an interrupt signal to the foreground process.

It is commonly used to stop a running command.

Example:

```bash
ping example.com
```

Press:

```
Ctrl+C
```

to interrupt the command.

---

Ctrl+Z

Ctrl+Z suspends the currently running foreground process.

Example:

```bash
ping example.com
```

Press:

```
Ctrl+Z
```

The process is stopped and becomes a shell job.

---

jobs

The jobs command displays jobs managed by the current shell.

```bash
jobs
```

Example output may show a stopped or background job.

---

fg — Foreground

The fg command brings a background or stopped job to the foreground.

```bash
fg
```

A specific job can be selected by its job number:

```bash
fg %1
```

---

bg — Background

The bg command resumes a stopped job in the background.

```bash
bg
```

A specific job can be selected:

```bash
bg %1
```

---

Background Processes

A command can also be started directly in the background by adding & to the end.

Example:

```bash
sleep 100 &
```

The shell returns control to the user while the command continues running in the background.

The running job can be viewed with:

```bash
jobs
```

---

Process Priority

Linux processes have a priority value that affects how the scheduler handles CPU time.

The nice value is used to influence process priority.

The renice command can change the nice value of an already running process.

---

renice

Change the nice value of a process:

```bash
renice 10 -p 1234
```

The command above changes the nice value of process 1234.

A process's priority information can be inspected using commands such as:

```bash
ps
```

or:

```bash
top
```

Process priority should be changed carefully because it can affect CPU scheduling.

---

Useful Commands

Command Purpose
ps Display process information
pstree Display processes as a tree
top Monitor processes in real time
htop Interactive process monitoring
pgrep Find processes by name or criteria
pidof Find PIDs associated with a program
kill Send a signal to a process
jobs Display shell jobs
fg Bring a job to the foreground
bg Resume a job in the background
renice Change the nice value of a running process

---

Practical Examples

Find a Process

```bash
pgrep bash
```

---

Inspect Processes

```bash
ps aux
```

---

Monitor Processes

```bash
top
```

or:

```bash
htop
```

---

Stop a Foreground Process

Run a command such as:

```bash
ping example.com
```

Then press:

```
Ctrl+C
```

---

Suspend and Resume a Process

Start a command:

```bash
ping example.com
```

Press:

```
Ctrl+Z
```

Check the job:

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

---

Terminate a Process

Find the PID:

```bash
pgrep process_name
```

Then send a termination signal:

```bash
kill PID
```

---

Key Takeaways

· Every running process has a PID.
· ps, top, and htop can be used to inspect running processes.
· pstree shows parent-child process relationships.
· pgrep and pidof can be used to find process IDs.
· Signals provide a way to communicate with or control processes.
· kill can send signals to processes.
· Ctrl+C interrupts a foreground process.
· Ctrl+Z suspends a foreground process.
· jobs, fg, and bg provide shell job control.
· renice can change the nice value of a running process.

---

Practice

These commands and concepts were studied as part of my Linux system administration learning.

The goal is to become comfortable with inspecting processes, understanding process states, controlling shell jobs, working with signals, and managing process priority.

---

Part of My-Note
Personal technical knowledge base — continuously updated.
