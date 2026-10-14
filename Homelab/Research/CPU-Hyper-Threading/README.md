# CPU Hyper-Threading

## Overview

Intel Hyper-Threading Technology (HTT) is a form of simultaneous multithreading (SMT). On supported processors, one physical CPU core can expose two logical processors to the operating system.

Logical processors are not additional physical cores. They share important execution resources within the same physical core, although each hardware thread maintains its own architectural state.

## Physical Cores vs. Logical CPUs

For a processor with four physical cores and Hyper-Threading enabled, the operating system will commonly see eight logical CPUs:

- **Physical cores:** The actual processing cores on the CPU.
- **Logical CPUs:** Hardware execution contexts the operating system can schedule work on.
- **Threads per core:** With Hyper-Threading enabled on a supported Intel CPU, this is commonly 2.

More logical CPUs do not mean performance will double. The benefit depends on the workload and how much the threads compete for shared core resources.

## How It Helps

If one hardware thread cannot use all of a core's execution resources at a given moment—for example, while waiting on data—the other thread may be able to make use of some available resources. This can improve throughput for some workloads.

Performance gains vary. Some workloads gain little, and contention for shared resources can limit or occasionally reduce performance.

## Why It Matters for Linux and Servers

Understanding physical cores and logical CPUs helps when checking hardware, monitoring performance, and planning workloads or virtual machines. Logical CPU count alone is not enough to predict server performance.

On Linux, inspect CPU topology with:

```bash
lscpu
```

Common fields include:

- `CPU(s)`: logical CPUs visible to the operating system.
- `Socket(s)`: processor sockets.
- `Core(s) per socket`: reported physical cores per socket.
- `Thread(s) per core`: hardware threads per core.

Example output interpretation: if a system reports 1 socket, 4 cores per socket, 2 threads per core, and 8 CPUs, it is exposing 8 logical CPUs across 4 physical cores. Actual output depends on the processor, firmware, and environment; virtual machines may report virtualized topology.

## Important Notes

- Hyper-Threading is an Intel brand name; the broader concept is simultaneous multithreading (SMT).
- Not every Intel CPU supports Hyper-Threading, and availability varies by processor generation and model.
- BIOS/UEFI settings and virtualization can affect the CPU topology visible to the operating system.
- Do not assume that twice as many logical CPUs means twice the computing power.

## Practical Verification

This note documents the concept. No CPU inspection or benchmark has been claimed as performed. The `lscpu` command can be used later to inspect the topology of a Linux system.

## References

- [Intel: Hyper-Threading Technology](https://www.intel.com/content/www/us/en/gaming/resources/hyper-threading.html)
- [Linux manual: lscpu](https://man7.org/linux/man-pages/man1/lscpu.1.html)
