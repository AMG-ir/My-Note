# 05 - Network Topologies

Network topology describes how devices and network connections are arranged. A topology can affect network performance, reliability, scalability, and troubleshooting.

## Overview

The topology types covered in this section:

- Bus (Linear)
- Ring
- Star
- Tree
- Full Mesh
- Partial Mesh

## Contents

- [Bus (Linear) Topology](#bus-linear-topology)
- [Ring Topology](#ring-topology)
- [Star Topology](#star-topology)
- [Tree Topology](#tree-topology)
- [Full Mesh Topology](#full-mesh-topology)
- [Partial Mesh Topology](#partial-mesh-topology)
- [Topology Comparison](#topology-comparison)
- [Choosing a Topology](#choosing-a-topology)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## Bus (Linear) Topology

In a bus topology, all devices share a single main communication line called the backbone.

```text
PC1 --- PC2 --- PC3 --- PC4 --- PC5
          Shared Backbone
```

**Characteristics**

- All devices connect to the same main cable.
- Data travels through the shared communication medium.
- A problem with the main backbone can affect the network.

**Advantages**

- Simple design
- Requires less cabling
- Can be inexpensive for small networks

**Disadvantages**

- Backbone failure can affect the entire network.
- Troubleshooting can be difficult.
- Performance can decrease as more devices are added.
- Limited scalability.

---

## Ring Topology

In a ring topology, each device is connected to two neighboring devices, forming a closed loop.

```text
      PC1
     /   \
   PC5   PC2
    |     |
   PC4---PC3
```

**Characteristics**

- Each device has two neighboring connections.
- The network forms a closed loop.
- Data travels around the ring according to the network design.

**Advantages**

- Organized communication path
- Each device has a defined position in the topology.
- Can provide predictable network performance.

**Disadvantages**

- A connection failure can affect communication.
- Adding or removing devices can be more complicated.
- Troubleshooting can be difficult.

---

## Star Topology

In a star topology, all devices connect to a central device. The central device is commonly a switch in modern Ethernet networks.

```text
             PC1
              |
              |
PC2 -------- Switch -------- PC3
              |
              |
             PC4
```

**Characteristics**

- Every device has a separate connection to the central device.
- The central device controls communication between connected devices.

**Advantages**

- Easy to manage
- Easy to troubleshoot
- Failure of one connection usually affects only one device.
- Easy to add or remove devices.
- Common in modern LANs.

**Disadvantages**

- Failure of the central device can affect connected devices.
- Requires more cabling than a bus topology.

---

## Tree Topology

A tree topology organizes multiple star-like networks into a hierarchical structure.

```text
                 Core
                  |
          +-------+-------+
        Switch          Switch
        /   \            /   \
      PC1   PC2        PC3   PC4
```

**Characteristics**

- Uses a hierarchical structure.
- Multiple network segments can be connected together.
- Higher-level devices connect lower-level segments.

**Advantages**

- Scalable
- Supports hierarchical network design
- Easier to organize large networks.
- Faults can sometimes be isolated to a specific branch.

**Disadvantages**

- Failure of an important higher-level device can affect multiple segments.
- More complex than a simple star topology.
- Requires careful planning.

---

## Full Mesh Topology

In a full mesh topology, every device has a direct connection to every other device.

```text
       PC1
      / | \
     /  |  \
   PC2--|--PC3
     \  |  /
      \ | /
       PC4
```

For n devices, the number of direct connections is:

```text
n(n - 1) / 2
```

For example, with 4 devices:

```text
4(4 - 1) / 2 = 6 connections
```

**Advantages**

- High redundancy
- Multiple communication paths
- Failure of one connection does not necessarily disconnect devices.
- High reliability

**Disadvantages**

- Requires a large amount of cabling or connections.
- Expensive
- Complex to configure and maintain.
- Does not scale efficiently as the number of devices increases.

---

## Partial Mesh Topology

In a partial mesh topology, only some devices have multiple direct connections. Not every device needs to connect directly to every other device.

```text
       PC1
      /   \
    PC2---PC3
           |
           |
          PC4
```

**Characteristics**

- Provides redundancy where it is needed.
- Uses fewer connections than a full mesh.
- Can combine reliability with lower cost.

**Advantages**

- More reliable than simple topologies.
- Less expensive than full mesh.
- Provides alternative paths between important devices.
- More scalable than full mesh.

**Disadvantages**

- More complex than star or bus.
- Requires network planning.
- Some devices may still depend on a limited number of paths.

---

## Topology Comparison

| Topology     | Main Structure                     | Reliability | Scalability | Complexity |
|--------------|------------------------------------|-------------|-------------|------------|
| Bus          | Shared backbone                    | Low         | Low         | Low |
| Ring         | Closed loop                        | Medium      | Medium      | Medium |
| Star         | Central device                     | High        | High        | Low |
| Tree         | Hierarchical                       | High        | High        | Medium |
| Full Mesh    | Every device connected             | Very High   | Low         | Very High |
| Partial Mesh | Selected redundant connections     | High        | High        | High |

---

## Choosing a Topology

The appropriate topology depends on factors such as:

- Number of devices
- Required reliability
- Cost
- Scalability
- Available cabling
- Network complexity
- Maintenance requirements

For example:

- Small simple networks may use a star-based design.
- Larger networks can use hierarchical tree structures.
- Critical network connections may use partial or full mesh designs for redundancy.

---

## Key Takeaways

- A topology describes how network devices and connections are arranged.
- Bus topology uses a shared backbone.
- Ring topology connects devices in a closed loop.
- Star topology connects devices to a central device.
- Tree topology uses a hierarchical structure.
- Full mesh provides a direct connection between every pair of devices.
- Partial mesh provides multiple connections only where needed.
- More redundancy usually means more cost and complexity.

---

## Practice

- Explain the difference between bus and star topology.
- Explain why star topology is common in LANs.
- Compare full mesh and partial mesh.
- Calculate the number of connections required for a full mesh with 5 devices.
- Explain one advantage and one disadvantage of tree topology.
- Compare the reliability of bus, star, and mesh topologies.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
