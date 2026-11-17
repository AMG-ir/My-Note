# Kernel and Architecture

How Linux separates applications from hardware, and how the kernel is designed.

## User Space and Kernel Space

- Everything a user runs (as a normal user or as an administrator) runs in **user space**.
- Applications never talk to the CPU, RAM, disk, or network directly. They send requests to the **kernel** through **system calls**.
- The kernel checks and handles the request, then talks to the hardware.
- This separation limits the damage of a bug or an exploited application: it cannot take over the whole system directly.

```text
Applications -> Shell -> User space
                         | system calls
                       Kernel space
                         |
                       Hardware (CPU, RAM, disk, network)
```

## System Calls

- System calls are functions written in C.
- A basic operating system needs roughly 150 to 180 of them, such as `open`, `exec`, and `close`.
- They let the kernel create, manage, and terminate processes, and allocate and free resources.

## Rings

- The architecture has privilege levels called **rings**.
- **Ring 0** is the lowest level and has the most access (the kernel).
- **Ring 3** is where applications run.

## What the Kernel Manages

- Processes (scheduling)
- Memory
- Devices and other hardware
- File systems (ext4, FAT, and others)
- Networking (TCP/IP and network cards)
- Inter-process communication (IPC)
- Security

### Process Scheduling

- The scheduler gives the CPU to one process at a time, switching between processes in tiny slices of time.
- That is why most processes in `top` are in the *sleeping* state and only one or very few are *running*.

## Shells

- The shell translates the commands a user types into instructions the kernel can run.
- Common shells: `bash` and `zsh`. Others have different history and small differences.

## Kernel Modules

- The kernel receives requests from user space and handles them through **kernel modules**.
- Writing custom kernel modules and enabling or disabling them is how an administrator customizes the system.

## Monolithic and Microkernel

| | Monolithic | Microkernel |
|---|-----------|-------------|
| Size | Larger | Smaller |
| Speed | Faster | Somewhat slower |
| Extending | Harder | Easier |
| Security and isolation | A fault in one component can affect the whole system | A crashed service does not affect the rest |

- Linux is monolithic.
- Microkernels are used in places such as IoT and industrial systems where isolation matters.
- Neither design is better in every case: it depends on the workload.

## Crashes

- On Windows a fatal error shows a BSOD (blue screen of death).
- On Linux the equivalent is a **kernel panic**.
- Both happen when the system cannot continue an operation, for example when it cannot read from RAM.

## Key Takeaways

- Applications reach hardware only through system calls to the kernel.
- Ring 0 is the kernel, ring 3 is applications.
- Linux is a monolithic kernel with kernel modules for customization.

## To Verify

- Which operating systems belong to each kernel design (the lecture mentioned several, but the details were unclear).
