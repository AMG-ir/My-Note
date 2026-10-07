Ethernet and IEEE 802

Ethernet is one of the most widely used technologies for wired Local Area Networks (LANs).

The IEEE 802 family contains standards related to networking, including Ethernet and wireless LAN technologies.

---

1. IEEE 802

IEEE 802 is a family of standards for Local and Metropolitan Area Networks.

Important standards include:

Standard Technology
IEEE 802.3 Ethernet
IEEE 802.11 Wireless LAN (Wi-Fi)
IEEE 802.1 LAN and network management standards

---

2. IEEE 802.3

IEEE 802.3 defines Ethernet standards.

Ethernet is commonly used to connect devices such as:

· Computers
· Servers
· Switches
· Routers
· Network devices

Example:

```text
PC1 ───────┐
           |
PC2 ─── Switch ─── Router
           |
PC3 ───────┘
```

---

3. Ethernet

Ethernet provides communication between devices on a wired network.

Ethernet primarily operates at:

· Physical Layer
· Data Link Layer

In the TCP/IP model, Ethernet belongs to the Network Access layer.

---

4. MAC Address

Ethernet devices use MAC addresses for communication at the Data Link layer.

A MAC address is normally represented as six hexadecimal pairs.

Example:

```text
00:1A:2B:3C:4D:5E
```

Another common notation is:

```text
00-1A-2B-3C-4D-5E
```

A MAC address is associated with a network interface.

---

5. Ethernet Frame

Ethernet transmits data using frames.

A simplified Ethernet frame contains fields such as:

```text
+-------------+-------------+--------+-------------+
| Destination |   Source    | Type   |    Data     |
| MAC Address | MAC Address |        |   Payload   |
+-------------+-------------+--------+-------------+
```

The destination MAC address identifies the intended destination on the local Ethernet network.

The source MAC address identifies the sender.

---

6. Ethernet and Switches

A switch uses MAC addresses to forward Ethernet frames.

Example:

```text
PC1 ─────┐
         |
PC2 ─── Switch ─── PC3
         |
PC4 ─────┘
```

The switch learns which MAC addresses are associated with its ports.

A simplified MAC address table can look like:

MAC Address Port
AA:AA:AA:AA:AA:01 Port 1
BB:BB:BB:BB:BB:02 Port 2
CC:CC:CC:CC:CC:03 Port 3

The switch can use this information to forward frames toward the correct port.

---

7. Unicast, Broadcast, and Multicast

Ethernet communication can be categorized by the destination.

Unicast

One sender communicates with one destination.

```text
PC1 ─────────> PC2
```

Broadcast

One sender communicates with all devices in the local broadcast domain.

```text
          ┌── PC2
          |
PC1 ───── Switch ─── PC3
          |
          └── PC4
```

Multicast

One sender communicates with a selected group of receivers.

```text
             ┌── PC2
             |
Sender ──────┼── PC3
             |
             └── PC4
```

---

8. Ethernet Speeds

Ethernet has developed through different speed standards.

Common examples include:

Technology Approximate Speed
Ethernet 10 Mbps
Fast Ethernet 100 Mbps
Gigabit Ethernet 1 Gbps
10 Gigabit Ethernet 10 Gbps

The actual speed depends on the Ethernet standard, cabling, and network hardware.

---

9. Ethernet Cables

Common Ethernet twisted-pair cable categories include:

· Cat5
· Cat5e
· Cat6
· Cat6a

These cables can support different network speeds and distances depending on the specific standard and installation.

A common Ethernet connector is:

```text
RJ-45
```

---

10. Full-Duplex Ethernet

Modern switched Ethernet commonly operates in full-duplex mode.

This allows a device to transmit and receive simultaneously.

```text
Device A ─────────────> Device B
Device A <───────────── Device B
```

Full-duplex communication helps avoid collisions that were associated with shared half-duplex Ethernet environments.

---

11. Collision Domain

A collision domain is a network area in which simultaneous transmissions can potentially interfere with each other.

Hubs create a shared collision domain.

With a switch, each switch port represents a separate collision domain in typical Ethernet operation.

```text
       PC1
        |
        |
      Switch
      /    \
    PC2    PC3
```

PC1, PC2, and PC3 are connected through separate switch ports.

---

12. Broadcast Domain

A broadcast domain is the set of devices that receive a Layer 2 broadcast.

A router can separate broadcast domains.

```text
Broadcast Domain A
        |
     Router
        |
Broadcast Domain B
```

---

13. IEEE 802.11

IEEE 802.11 is the family of standards used for Wireless LANs.

It is commonly associated with Wi-Fi.

```text
Laptop
   |
 Wi-Fi
   |
Access Point
   |
Network
```

IEEE 802.11 includes different generations and amendments that operate using different frequencies, capabilities, and technologies.

---

14. 2.4 GHz and 5 GHz

Wi-Fi networks commonly operate in the 2.4 GHz and 5 GHz bands.

2.4 GHz

Characteristics include:

· Longer typical range
· Better ability to pass through obstacles
· More potential interference
· Fewer available non-overlapping channels

5 GHz

Characteristics include:

· Higher available performance in many conditions
· More available channels
· Generally less range than 2.4 GHz
· More affected by obstacles

The actual performance depends on the environment, hardware, channel configuration, and other factors.

---

15. Ethernet vs Wi-Fi

Feature Ethernet Wi-Fi
Connection Wired Wireless
Standard IEEE 802.3 IEEE 802.11
Medium Cable Radio
Mobility Limited High
Interference Generally lower More susceptible
Common Device Switch Access Point

---

16. Ethernet and TCP/IP

Ethernet provides network access functionality for TCP/IP communication.

Example:

```text
Application
     |
   TCP/UDP
     |
     IP
     |
 Ethernet
     |
Physical Medium
```

The application data is encapsulated as it moves through the networking layers.

---

Key Takeaways

· IEEE 802 is a family of networking standards.
· IEEE 802.3 defines Ethernet.
· IEEE 802.11 defines Wireless LAN technologies.
· Ethernet is widely used for wired LANs.
· Ethernet uses MAC addresses at the Data Link layer.
· Ethernet transmits data using frames.
· Switches use MAC addresses to forward Ethernet frames.
· Ethernet communication can be unicast, broadcast, or multicast.
· Modern switched Ethernet commonly uses full-duplex communication.
· A hub creates a shared collision domain.
· A router separates broadcast domains.
· 2.4 GHz and 5 GHz are commonly used Wi-Fi frequency bands.
· Ethernet and Wi-Fi provide different methods of network access.

---

Practice

1. What is IEEE 802?
2. What standard defines Ethernet?
3. What standard is associated with Wi-Fi?
4. What is a MAC address?
5. What is the purpose of an Ethernet frame?
6. Explain the difference between unicast, broadcast, and multicast.
7. Compare 2.4 GHz and 5 GHz.
8. What is a collision domain?
9. What is a broadcast domain?
10. Explain the difference between IEEE 802.3 and IEEE 802.11.
