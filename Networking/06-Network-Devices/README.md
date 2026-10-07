Network Devices

Network devices are hardware components used to connect, control, forward, or manage communication between devices and networks.

This section covers the main network devices and their basic roles.

---

1. Network Interface Card (NIC)

A Network Interface Card (NIC) provides a device with network connectivity.

A NIC can provide:

· Wired Ethernet connectivity
· Wireless connectivity

Each network interface has a MAC address used for communication at the data-link level.

---

2. Hub

A hub is a basic network device that connects multiple devices.

When a hub receives data, it forwards the data to all connected ports.

```text
             PC1
              |
              |
PC2 -------- Hub -------- PC3
              |
              |
             PC4
```

Characteristics

· Operates mainly at Layer 1.
· Does not intelligently select the destination device.
· Sends incoming traffic to connected ports.
· All connected devices share the communication medium.

Advantages

· Simple
· Easy to use
· Low complexity

Disadvantages

· Sends traffic to all ports.
· Creates unnecessary network traffic.
· Less efficient than a switch.
· Can result in collisions.

---

3. Switch

A switch connects devices within a local network and forwards Ethernet frames toward the appropriate destination.

```text
             PC1
              |
              |
PC2 -------- Switch -------- PC3
              |
              |
             PC4
```

A switch uses MAC addresses to make forwarding decisions.

Characteristics

· Commonly operates at Layer 2.
· Maintains a MAC address table.
· Provides a dedicated connection between a port and the connected device.
· Commonly used in LANs.

Advantages

· More efficient than a hub.
· Reduces unnecessary traffic.
· Supports multiple connected devices.
· Common in modern Ethernet networks.

Types of Switches

Some common switch categories include:

· Unmanaged switch
· Managed switch
· Layer 2 switch
· Layer 3 switch

---

4. Router

A router connects different networks and forwards packets between them.

```text
LAN 1
  |
  |
Router
  |
  |
LAN 2
```

A router makes forwarding decisions using IP addresses and routing information.

Characteristics

· Operates primarily at Layer 3.
· Connects different networks.
· Uses routing information to determine where packets should go.
· Can provide communication between separate IP networks.

Example

A home router can connect:

```text
Local Network
      |
      |
   Router
      |
      |
  Internet
```

---

5. Bridge

A bridge connects network segments and forwards traffic between them.

```text
Network A
   |
Bridge
   |
Network B
```

Characteristics

· Primarily associated with Layer 2.
· Uses MAC addresses.
· Can divide a network into separate segments.
· A switch can be considered a more advanced form of bridging technology.

---

6. Gateway

A gateway provides a way for communication between different networks or systems.

The term "gateway" can have different meanings depending on the context.

In IP networking, a default gateway is the device that a host uses to reach networks outside its local network.

```text
PC
 |
 |
Default Gateway
 |
 |
Other Network
```

Default Gateway

For example:

```text
PC:              192.168.1.10
Default Gateway: 192.168.1.1
```

When the destination is outside the local network, the host can send the traffic toward the default gateway.

---

7. Access Point

An Access Point (AP) provides wireless devices with access to a network.

```text
        Laptop
          |
       Wi-Fi
          |
     Access Point
          |
       Switch
          |
       Network
```

Characteristics

· Provides wireless network connectivity.
· Connects wireless clients to a wired network.
· Commonly used in Wi-Fi networks.

---

Device Comparison

Device Main Role Common Layer Addressing
NIC Provides network connectivity Layer 1/2 MAC
Hub Connects devices and repeats traffic Layer 1 No intelligent addressing
Switch Connects devices in a LAN Layer 2 MAC
Router Connects different networks Layer 3 IP
Bridge Connects network segments Layer 2 MAC
Gateway Provides access to another network/system Depends on implementation Depends on implementation
Access Point Provides wireless network access Layer 2 MAC

---

Hub vs Switch

Feature Hub Switch
Main Layer Layer 1 Layer 2
Forwarding All ports Destination port
Uses MAC Address Table No Yes
Efficiency Lower Higher
Common in modern LANs Rare Very common

---

Switch vs Router

Feature Switch Router
Main Purpose Connect devices in a LAN Connect different networks
Main Layer Layer 2 Layer 3
Main Address MAC IP
Typical Use Local network communication Communication between networks

---

Key Takeaways

· A NIC provides network connectivity to a device.
· A hub forwards traffic to all connected ports.
· A switch uses MAC addresses to forward Ethernet traffic.
· A router connects different networks and uses IP addresses.
· A bridge connects network segments at Layer 2.
· A gateway provides a path to another network or system.
· An Access Point provides wireless access to a network.

---

Practice

1. Explain the difference between a hub and a switch.
2. Explain why a switch uses MAC addresses.
3. Explain the difference between a switch and a router.
4. What is the role of a default gateway?
5. Explain the purpose of a bridge.
6. What is the main purpose of an Access Point?
7. Match each device with its main purpose:
   · Hub
   · Switch
   · Router
   · Bridge
   · Gateway
   · Access Point
