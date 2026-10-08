# 10 - Ethernet and IEEE 802

Ethernet is one of the most widely used technologies for wired Local Area Networks (LANs). The IEEE 802 family contains standards related to networking, including Ethernet and wireless LAN technologies.

## Contents

- [IEEE 802](#ieee-802)
- [IEEE 802.3](#ieee-8023)
- [Ethernet](#ethernet)
- [MAC Address](#mac-address)
- [Ethernet Frame](#ethernet-frame)
- [Ethernet and Switches](#ethernet-and-switches)
- [Unicast, Broadcast, and Multicast](#unicast-broadcast-and-multicast)
- [Ethernet Speeds](#ethernet-speeds)
- [Ethernet Cables](#ethernet-cables)
- [Full-Duplex Ethernet](#full-duplex-ethernet)
- [Collision Domain](#collision-domain)
- [Broadcast Domain](#broadcast-domain)
- [IEEE 802.11](#ieee-80211)
- [2.4 GHz and 5 GHz](#24-ghz-and-5-ghz)
- [Ethernet vs Wi-Fi](#ethernet-vs-wi-fi)
- [Ethernet and TCP/IP](#ethernet-and-tcpip)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## IEEE 802

IEEE 802 is a family of standards for Local and Metropolitan Area Networks. Important standards include:

| Standard   | Technology |
|------------|------------|
| IEEE 802.3  | Ethernet |
| IEEE 802.11 | Wireless LAN (Wi-Fi) |
| IEEE 802.1  | LAN and network management standards |

---

## IEEE 802.3

IEEE 802.3 defines Ethernet standards. Ethernet is commonly used to connect devices such as computers, servers, switches, routers, and other network devices.

```text
PC1 -------+
           |
PC2 --- Switch --- Router
           |
PC3 -------+
```

---

## Ethernet

Ethernet provides communication between devices on a wired network. It primarily operates at the Physical and Data Link layers. In the TCP/IP model, Ethernet belongs to the Network Access layer.

---

## MAC Address

Ethernet devices use MAC addresses for communication at the Data Link layer. A MAC address is normally represented as six hexadecimal pairs.

```text
00:1A:2B:3C:4D:5E
```

Another common notation:

```text
00-1A-2B-3C-4D-5E
```

A MAC address is associated with a network interface.

---

## Ethernet Frame

Ethernet transmits data using frames. A simplified Ethernet frame contains fields such as:

```text
+-------------+-------------+--------+-------------+
| Destination |   Source    | Type   |    Data     |
| MAC Address | MAC Address |        |   Payload   |
+-------------+-------------+--------+-------------+
```

The destination MAC address identifies the intended destination on the local Ethernet network. The source MAC address identifies the sender.

---

## Ethernet and Switches

A switch uses MAC addresses to forward Ethernet frames.

```text
PC1 -----+
         |
PC2 --- Switch --- PC3
         |
PC4 -----+
```

The switch learns which MAC addresses are associated with its ports. A simplified MAC address table:

| MAC Address         | Port   |
|---------------------|--------|
| AA:AA:AA:AA:AA:01   | Port 1 |
| BB:BB:BB:BB:BB:02   | Port 2 |
| CC:CC:CC:CC:CC:03   | Port 3 |

The switch can use this information to forward frames toward the correct port.

---

## Unicast, Broadcast, and Multicast

Ethernet communication can be categorized by the destination.

### Unicast

One sender communicates with one destination.

```text
PC1 ---------> PC2
```

### Broadcast

One sender communicates with all devices in the local broadcast domain.

```text
          +-- PC2
          |
PC1 ----- Switch --- PC3
          |
          +-- PC4
```

### Multicast

One sender communicates with a selected group of receivers.

```text
             +-- PC2
             |
Sender ------+-- PC3
             |
             +-- PC4
```

---

## Ethernet Speeds

Ethernet has developed through different speed standards.

| Technology          | Approximate Speed |
|---------------------|-------------------|
| Ethernet            | 10 Mbps |
| Fast Ethernet       | 100 Mbps |
| Gigabit Ethernet    | 1 Gbps |
| 10 Gigabit Ethernet | 10 Gbps |

The actual speed depends on the Ethernet standard, cabling, and network hardware.

---

## Ethernet Cables

Common Ethernet twisted-pair cable categories include:

- Cat5
- Cat5e
- Cat6
- Cat6a

These cables can support different network speeds and distances depending on the specific standard and installation. A common Ethernet connector is RJ-45.

---

## Full-Duplex Ethernet

Modern switched Ethernet commonly operates in full-duplex mode. This allows a device to transmit and receive simultaneously.

```text
Device A ---------------> Device B
Device A <--------------- Device B
```

Full-duplex communication helps avoid collisions that were associated with shared half-duplex Ethernet environments.

---

## Collision Domain

A collision domain is a network area in which simultaneous transmissions can potentially interfere with each other. Hubs create a shared collision domain. With a switch, each switch port represents a separate collision domain in typical Ethernet operation.

```text
       PC1
        |
      Switch
      /    \
    PC2    PC3
```

PC1, PC2, and PC3 are connected through separate switch ports.

---

## Broadcast Domain

A broadcast domain is the set of devices that receive a Layer 2 broadcast. A router can separate broadcast domains.

```text
Broadcast Domain A
        |
     Router
        |
Broadcast Domain B
```

---

## IEEE 802.11

IEEE 802.11 is the family of standards used for Wireless LANs. It is commonly associated with Wi-Fi.

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

## 2.4 GHz and 5 GHz

Wi-Fi networks commonly operate in the 2.4 GHz and 5 GHz bands.

**2.4 GHz**

- Longer typical range
- Better ability to pass through obstacles
- More potential interference
- Fewer available non-overlapping channels

**5 GHz**

- Higher available performance in many conditions
- More available channels
- Generally less range than 2.4 GHz
- More affected by obstacles

> **Note:** The actual performance depends on the environment, hardware, channel configuration, and other factors.

---

## Ethernet vs Wi-Fi

| Feature       | Ethernet     | Wi-Fi |
|---------------|--------------|-------|
| Connection    | Wired        | Wireless |
| Standard      | IEEE 802.3   | IEEE 802.11 |
| Medium        | Cable        | Radio |
| Mobility      | Limited      | High |
| Interference  | Generally lower | More susceptible |
| Common Device | Switch       | Access Point |

---

## Ethernet and TCP/IP

Ethernet provides network access functionality for TCP/IP communication.

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

## Key Takeaways

- IEEE 802 is a family of networking standards.
- IEEE 802.3 defines Ethernet.
- IEEE 802.11 defines Wireless LAN technologies.
- Ethernet is widely used for wired LANs.
- Ethernet uses MAC addresses at the Data Link layer.
- Ethernet transmits data using frames.
- Switches use MAC addresses to forward Ethernet frames.
- Ethernet communication can be unicast, broadcast, or multicast.
- Modern switched Ethernet commonly uses full-duplex communication.
- A hub creates a shared collision domain.
- A router separates broadcast domains.
- 2.4 GHz and 5 GHz are commonly used Wi-Fi frequency bands.
- Ethernet and Wi-Fi provide different methods of network access.

---

## Practice

- What is IEEE 802?
- What standard defines Ethernet?
- What standard is associated with Wi-Fi?
- What is a MAC address?
- What is the purpose of an Ethernet frame?
- Explain the difference between unicast, broadcast, and multicast.
- Compare 2.4 GHz and 5 GHz.
- What is a collision domain?
- What is a broadcast domain?
- Explain the difference between IEEE 802.3 and IEEE 802.11.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
