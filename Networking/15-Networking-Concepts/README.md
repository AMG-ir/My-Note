# 15 - Networking Concepts

This section covers additional networking concepts that connect the fundamental topics of networking, network models, devices, addressing, protocols, wireless networking, segmentation, security, and cryptography.

## Contents

- [Network Communication](#network-communication)
- [Host](#host)
- [Client and Server](#client-and-server)
- [Peer-to-Peer](#peer-to-peer)
- [Network Addressing](#network-addressing)
- [Default Gateway](#default-gateway)
- [Routing and Switching](#routing-and-switching)
- [Unicast, Broadcast, and Multicast](#unicast-broadcast-and-multicast)
- [Bandwidth and Latency](#bandwidth-and-latency)
- [Reliability and Redundancy](#reliability-and-redundancy)
- [Network Performance](#network-performance)
- [Network Troubleshooting Approach](#network-troubleshooting-approach)
- [Segmentation, Security, and DMZ](#segmentation-security-and-dmz)
- [Network Communication Summary](#network-communication-summary)
- [Important Concepts Comparison](#important-concepts-comparison)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## Network Communication

Network communication is the exchange of data between devices over a network.

```text
Source Device
     |
     v
Network
     |
     v
Destination Device
```

Communication between systems depends on several components, including:

- Network interfaces
- Transmission media
- Network devices
- Protocols
- Addresses
- Network services

---

## Host

A host is a device connected to a network that can send or receive data. Examples include:

- Computers
- Servers
- Network-enabled devices
- Other systems participating in network communication

A host can have a network address that identifies it within a network.

---

## Client and Server

Network communication commonly uses the client-server model. A client is a system that requests a service or resource. A server is a system that provides a service or resource.

```text
Client
  |
  | Request
  v
Server
  |
  | Response
  v
Client
```

Examples include:

- Web clients communicating with web servers
- Email clients communicating with mail servers
- Network systems communicating with service servers

---

## Peer-to-Peer

In a peer-to-peer network, systems can communicate directly with each other without requiring a dedicated central server for every interaction.

```text
Peer <----> Peer
  ^            ^
  |            |
  +------------+
```

Each peer can participate directly in network communication.

---

## Network Addressing

Network addressing allows devices and interfaces to be identified within a network. Two important addressing concepts are the MAC address and the IP address.

```text
MAC Address -> Local network identification
IP Address  -> Logical network addressing
```

| Feature         | MAC Address                   | IP Address |
|-----------------|-------------------------------|------------|
| Type            | Hardware/interface address    | Logical address |
| Main use        | Local network communication   | Network communication |
| Associated with | Network interface             | Network configuration |
| Layer           | Data Link                     | Network |

---

## Default Gateway

A default gateway is the device used by a host to reach destinations outside its local network. A router commonly performs the role of a default gateway.

```text
Local Host
    |
    v
Default Gateway
    |
    v
Other Network
```

---

## Routing and Switching

### Routing

Routing is the process of determining how packets travel from one network to another. A router uses routing information to select a path toward a destination.

```text
Network A
    |
    v
 Router
    |
    v
Network B
```

### Switching

Switching is the process of forwarding frames within a network. A switch uses MAC addresses to determine where frames should be forwarded. Switching is primarily associated with the Data Link layer.

```text
PC 1 ----+
         |
PC 2 --- Switch --- PC 3
         |
PC 4 ----+
```

### Switching vs Routing

| Feature      | Switching                        | Routing |
|--------------|----------------------------------|---------|
| Main unit    | Frame                            | Packet |
| Main address | MAC address                      | IP address |
| Common device| Switch                           | Router |
| Main purpose | Communication within a network   | Communication between networks |

---

## Unicast, Broadcast, and Multicast

### Unicast

One-to-one communication.

```text
Sender ----------------> Receiver
```

### Broadcast

Communication intended for all devices within a relevant broadcast domain. Broadcast traffic can be limited through network segmentation.

```text
             Device
                ^
                |
Device <---- Broadcast ----> Device
                |
                v
             Device
```

### Multicast

Data sent from one source to a specific group of receivers. Only members of the relevant multicast group receive the traffic.

```text
             Receiver
                ^
                |
Sender ---------+--------> Receiver
                |
                v
             Receiver
```

### Comparison

| Type      | Communication |
|-----------|---------------|
| Unicast   | One-to-one |
| Broadcast | One-to-all within the relevant broadcast domain |
| Multicast | One-to-selected group |

---

## Bandwidth and Latency

**Bandwidth** refers to the capacity of a communication link to carry data. Higher bandwidth generally allows more data to be transferred during a given period. It is commonly expressed in bps, Kbps, Mbps, and Gbps.

**Latency** is the delay involved in transmitting data between two points. A network can have high bandwidth while still experiencing high latency. Latency is especially important for applications that require fast responses.

```text
Source
  |
  |------ Network ------|
                         |
                    Destination

        <--- Delay --->
```

| Concept   | Meaning |
|-----------|---------|
| Bandwidth | Data-carrying capacity |
| Latency   | Communication delay |

> **Note:** A network with high bandwidth does not necessarily have low latency.

---

## Reliability and Redundancy

Network reliability refers to the ability of a network to continue operating correctly and provide communication when required. Reliability can be improved through:

- Redundant connections
- Multiple network paths
- Backup devices
- Proper network design

Redundancy means having additional components or paths that can provide service if another component fails.

```text
        Router A
       /        \
Network -------- Network
       \        /
        Router B
```

Redundancy can reduce the impact of individual failures.

---

## Network Performance

Network performance can be affected by several factors, including:

- Bandwidth
- Latency
- Network congestion
- Distance
- Hardware
- Transmission medium
- Network configuration

### Network Congestion

Network congestion occurs when network traffic becomes greater than the available capacity. When traffic exceeds available capacity, performance can decrease. Possible effects include:

- Increased latency
- Packet loss
- Reduced performance

### Packet Loss

Packet loss occurs when packets do not successfully reach their destination. Possible causes include:

- Network congestion
- Hardware problems
- Configuration problems
- Unstable network connections

Packet loss can negatively affect network performance.

---

## Network Troubleshooting Approach

A basic troubleshooting process can be performed from the lower layers toward the higher layers.

```text
Physical Connection
        |
        v
Network Interface
        |
        v
IP Configuration
        |
        v
Connectivity
        |
        v
Routing
        |
        v
Services
```

Useful questions include:

1. Is the network interface working?
2. Does the device have the correct network configuration?
3. Can the local network be reached?
4. Can the destination be reached?
5. Is routing working correctly?
6. Is the required service available?

---

## Segmentation, Security, and DMZ

### Network Segmentation

Network segmentation divides a network into separate logical or physical sections. It can be used to control traffic, reduce unnecessary traffic, improve security, and separate different network areas. Examples include LAN segmentation, DMZ, and firewall-based segmentation.

### Network Security and Defense

Network security protects network resources and communication against unauthorized access and attacks. Important concepts include:

- Authentication
- Authorization
- Firewalls
- Encryption
- Hashing
- Network segmentation
- Access control

Security should be considered as part of the overall network design.

### Internet, Intranet, and DMZ

- **Internet:** a public global network connecting many independent networks.
- **Intranet:** a private network used within an organization.
- **DMZ:** a separated network area used for systems that need to provide services while remaining isolated from the internal network.

```text
Internet
    |
    v
Firewall
    |
    +------ DMZ
    |
    v
Internal Network
```

---

## Network Communication Summary

A simplified network communication process:

```text
Application
    |
    v
Transport
    |
    v
Network
    |
    v
Data Link
    |
    v
Physical
```

Data is processed through different networking layers before being transmitted through the network.

---

## Important Concepts Comparison

| Concept       | Main Idea |
|---------------|-----------|
| Client        | Requests a service |
| Server        | Provides a service |
| Peer-to-Peer  | Direct communication between peers |
| Switching     | Forwarding frames within a network |
| Routing       | Forwarding packets between networks |
| Bandwidth     | Data-carrying capacity |
| Latency       | Communication delay |
| Broadcast     | One-to-all communication |
| Unicast       | One-to-one communication |
| Multicast     | One-to-group communication |
| Redundancy    | Additional components or paths |
| Segmentation  | Dividing a network into separate areas |

---

## Key Takeaways

- Hosts communicate through network interfaces, protocols, and network devices.
- Clients request services and servers provide them.
- MAC addresses and IP addresses serve different purposes.
- Switches primarily forward frames using MAC addresses.
- Routers forward packets between networks using IP addressing and routing information.
- A default gateway provides a path toward other networks.
- Unicast, broadcast, and multicast describe different communication patterns.
- Bandwidth and latency are different aspects of network performance.
- Congestion and packet loss can negatively affect communication.
- Redundancy can improve network reliability.
- Network segmentation can improve both performance and security.
- A structured troubleshooting process helps identify network problems.

---

## Practice

- Explain the difference between a client and a server.
- Explain peer-to-peer communication.
- What is the difference between a MAC address and an IP address?
- What is the purpose of a default gateway?
- Explain the difference between switching and routing.
- What is the difference between unicast, broadcast, and multicast?
- Explain the difference between bandwidth and latency.
- What is network congestion?
- What is packet loss?
- Why is network segmentation useful?
- Explain the purpose of a DMZ.
- Describe a basic network troubleshooting process.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
