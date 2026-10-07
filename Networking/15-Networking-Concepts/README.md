Networking Concepts

This section covers additional networking concepts that connect the fundamental topics of networking, network models, devices, addressing, protocols, wireless networking, segmentation, security, and cryptography.

1. Network Communication

Network communication is the exchange of data between devices over a network.

A basic communication path can include:

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

· Network interfaces
· Transmission media
· Network devices
· Protocols
· Addresses
· Network services

---

2. Host

A host is a device connected to a network that can send or receive data.

Examples include:

· Computers
· Servers
· Network-enabled devices
· Other systems participating in network communication

A host can have a network address that identifies it within a network.

---

3. Client and Server

Network communication commonly uses the client-server model.

Client

A client is a system that requests a service or resource.

Server

A server is a system that provides a service or resource.

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

· Web clients communicating with web servers
· Email clients communicating with mail servers
· Network systems communicating with service servers

---

4. Peer-to-Peer

In a peer-to-peer network, systems can communicate directly with each other without requiring a dedicated central server for every interaction.

```text
Peer <----> Peer
  ^            ^
  |            |
  +------------+
```

Each peer can participate directly in network communication.

---

5. Network Addressing

Network addressing allows devices and interfaces to be identified within a network.

Two important addressing concepts are:

· MAC address
· IP address

MAC Address

A MAC address is associated with a network interface and operates at the Data Link layer.

IP Address

An IP address is used for logical network addressing and communication between networks.

```text
MAC Address -> Local network identification
IP Address  -> Logical network addressing
```

---

6. MAC Address vs IP Address

Feature MAC Address IP Address
Type Hardware/interface address Logical address
Main use Local network communication Network communication
Associated with Network interface Network configuration
Layer Data Link Network

---

7. Default Gateway

A default gateway is the device used by a host to reach destinations outside its local network.

```text
Local Host
    |
    v
Default Gateway
    |
    v
Other Network
```

A router commonly performs the role of a default gateway.

---

8. Routing

Routing is the process of determining how packets travel from one network to another.

A router uses routing information to select a path toward a destination.

```text
Network A
    |
    v
 Router
    |
    v
Network B
```

Routing is an important part of communication between different networks.

---

9. Switching

Switching is the process of forwarding frames within a network.

A switch uses MAC addresses to determine where frames should be forwarded.

```text
PC 1 ----\
           \
PC 2 ------ Switch ------ PC 3
           /
PC 4 ----/
```

Switching is primarily associated with the Data Link layer.

---

10. Switching vs Routing

Feature Switching Routing
Main unit Frame Packet
Main address MAC address IP address
Common device Switch Router
Main purpose Communication within a network Communication between networks

---

11. Broadcast

A broadcast is communication intended for all devices within a relevant broadcast domain.

```text
             Device
                ^
                |
Device <---- Broadcast ----> Device
                |
                v
             Device
```

Broadcast traffic can be limited through network segmentation.

---

12. Unicast

Unicast communication is one-to-one communication.

```text
Sender ----------------> Receiver
```

The sender communicates with a specific destination.

---

13. Multicast

Multicast communication allows data to be sent from one source to a specific group of receivers.

```text
             Receiver
                ^
                |
Sender ---------+--------> Receiver
                |
                v
             Receiver
```

Only members of the relevant multicast group receive the traffic.

---

14. Unicast vs Broadcast vs Multicast

Type Communication
Unicast One-to-one
Broadcast One-to-all within the relevant broadcast domain
Multicast One-to-selected group

---

15. Bandwidth

Bandwidth refers to the capacity of a communication link to carry data.

Higher bandwidth generally allows more data to be transferred during a given period.

Bandwidth is commonly expressed using units such as:

· bps
· Kbps
· Mbps
· Gbps

---

16. Latency

Latency is the delay involved in transmitting data between two points.

A network can have high bandwidth while still experiencing high latency.

```text
Source
  |
  |------ Network ------|
                         |
                      Destination

        <--- Delay --->
```

Latency is especially important for applications that require fast responses.

---

17. Bandwidth vs Latency

Concept Meaning
Bandwidth Data-carrying capacity
Latency Communication delay

A network with high bandwidth does not necessarily have low latency.

---

18. Network Reliability

Network reliability refers to the ability of a network to continue operating correctly and provide communication when required.

Reliability can be improved through concepts such as:

· Redundant connections
· Multiple network paths
· Backup devices
· Proper network design

---

19. Redundancy

Redundancy means having additional components or paths that can provide service if another component fails.

Example:

```text
        Router A
       /        \
Network -------- Network
       \        /
        Router B
```

Redundancy can reduce the impact of individual failures.

---

20. Network Performance

Network performance can be affected by several factors, including:

· Bandwidth
· Latency
· Network congestion
· Distance
· Hardware
· Transmission medium
· Network configuration

Understanding these factors helps when analyzing network behavior.

---

21. Network Congestion

Network congestion occurs when network traffic becomes greater than the available capacity.

```text
Normal Traffic
      |
      v
Network Capacity
      |
      v
Normal Communication
```

When traffic exceeds available capacity, performance can decrease.

Possible effects include:

· Increased latency
· Packet loss
· Reduced performance

---

22. Packet Loss

Packet loss occurs when packets do not successfully reach their destination.

Possible causes include:

· Network congestion
· Hardware problems
· Configuration problems
· Unstable network connections

Packet loss can negatively affect network performance.

---

23. Network Troubleshooting Approach

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

24. Network Segmentation

Network segmentation divides a network into separate logical or physical sections.

Segmentation can be used to:

· Control traffic
· Reduce unnecessary traffic
· Improve security
· Separate different network areas

Examples include:

· LAN segmentation
· DMZ
· Firewall-based segmentation

---

25. Network Security and Defense

Network security protects network resources and communication against unauthorized access and attacks.

Important concepts include:

· Authentication
· Authorization
· Firewalls
· Encryption
· Hashing
· Network segmentation
· Access control

Security should be considered as part of the overall network design.

---

26. Internet, Intranet, and DMZ

Internet

A public global network connecting many independent networks.

Intranet

A private network used within an organization.

DMZ

A separated network area used for systems that need to provide services while remaining isolated from the internal network.

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

27. Network Communication Summary

A simplified network communication process can be represented as:

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

28. Important Concepts Comparison

Concept Main Idea
Client Requests a service
Server Provides a service
Peer-to-Peer Direct communication between peers
Switching Forwarding frames within a network
Routing Forwarding packets between networks
Bandwidth Data-carrying capacity
Latency Communication delay
Broadcast One-to-all communication
Unicast One-to-one communication
Multicast One-to-group communication
Redundancy Additional components or paths
Segmentation Dividing a network into separate areas

---

Key Takeaways

· Hosts communicate through network interfaces, protocols, and network devices.
· Clients request services and servers provide them.
· MAC addresses and IP addresses serve different purposes.
· Switches primarily forward frames using MAC addresses.
· Routers forward packets between networks using IP addressing and routing information.
· A default gateway provides a path toward other networks.
· Unicast, broadcast, and multicast describe different communication patterns.
· Bandwidth and latency are different aspects of network performance.
· Congestion and packet loss can negatively affect communication.
· Redundancy can improve network reliability.
· Network segmentation can improve both performance and security.
· A structured troubleshooting process helps identify network problems.

---

Practice

1. Explain the difference between a client and a server.
2. Explain peer-to-peer communication.
3. What is the difference between a MAC address and an IP address?
4. What is the purpose of a default gateway?
5. Explain the difference between switching and routing.
6. What is the difference between unicast, broadcast, and multicast?
7. Explain the difference between bandwidth and latency.
8. What is network congestion?
9. What is packet loss?
10. Why is network segmentation useful?
11. Explain the purpose of a DMZ.
12. Describe a basic network troubleshooting process.
