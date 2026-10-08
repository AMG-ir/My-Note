# 02 - OSI Model

The OSI (Open Systems Interconnection) model is a conceptual reference model used to understand how network communication works.

## Overview

The OSI model divides network communication into seven layers. Each layer has a specific role and works with the layers above and below it.

## Contents

- [The Seven OSI Layers](#the-seven-osi-layers)
- [Layer 1 - Physical](#layer-1---physical)
- [Layer 2 - Data Link](#layer-2---data-link)
- [Layer 3 - Network](#layer-3---network)
- [Layer 4 - Transport](#layer-4---transport)
- [Layer 5 - Session](#layer-5---session)
- [Layer 6 - Presentation](#layer-6---presentation)
- [Layer 7 - Application](#layer-7---application)
- [OSI Layers and Data Units](#osi-layers-and-data-units)
- [Encapsulation and Decapsulation](#encapsulation-and-decapsulation)
- [Layer-to-Layer Communication](#layer-to-layer-communication)
- [OSI Model and Network Devices](#osi-model-and-network-devices)
- [MAC Address and IP Address](#mac-address-and-ip-address)
- [OSI Model and Troubleshooting](#osi-model-and-troubleshooting)
- [Layer Summary](#layer-summary)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## The Seven OSI Layers

From the highest layer to the lowest:

```text
Layer 7 - Application
Layer 6 - Presentation
Layer 5 - Session
Layer 4 - Transport
Layer 3 - Network
Layer 2 - Data Link
Layer 1 - Physical
```

---

## Layer 1 - Physical

The Physical layer is responsible for the transmission of raw bits over a physical medium. It deals with the physical characteristics of network communication.

Examples include:

- Cables
- Connectors
- Radio signals
- Electrical signals
- Optical signals
- Physical transmission media

The Physical layer does not understand IP addresses or application data. It deals with the transmission of bits.

```text
Bits -> Physical Medium -> Bits
```

---

## Layer 2 - Data Link

The Data Link layer provides communication between devices on the same network segment.

Important concepts include:

- MAC addresses
- Frames
- Ethernet
- Switches
- Error detection
- Local network communication

The Data Link layer works with frames.

```text
Data -> Frame -> Data
```

MAC addresses are primarily associated with Layer 2.

---

## Layer 3 - Network

The Network layer is responsible for logical addressing and routing between networks.

Important concepts include:

- IP addresses
- Routing
- Packets
- Routers
- Network-to-network communication

The Network layer works with packets.

```text
Data -> Packet -> Data
```

IP is a major protocol associated with this layer.

---

## Layer 4 - Transport

The Transport layer provides end-to-end communication between applications.

Important concepts include:

- TCP
- UDP
- Ports
- Segmentation
- Reliability
- Flow control

TCP provides reliable, connection-oriented communication. UDP provides connectionless communication with lower protocol overhead.

The Transport layer works with segments when using TCP and commonly with datagrams when using UDP.

---

## Layer 5 - Session

The Session layer manages communication sessions between applications. Its responsibilities can include:

- Establishing sessions
- Managing sessions
- Maintaining sessions
- Terminating sessions

---

## Layer 6 - Presentation

The Presentation layer deals with how data is represented. Its responsibilities can include:

- Data formatting
- Data translation
- Encryption and decryption
- Compression and decompression

The layer helps ensure that data can be interpreted correctly by the receiving system.

---

## Layer 7 - Application

The Application layer is the layer closest to the user and provides network services to applications.

Examples of protocols associated with this layer include:

- HTTP
- HTTPS
- FTP
- SSH
- DNS
- SMTP
- POP3
- IMAP

> **Note:** The Application layer does not mean the application itself. It provides network functionality used by applications.

---

## OSI Layers and Data Units

Different layers use different terms to describe the data being handled.

| Layer | Name         | Data Unit            |
|-------|--------------|----------------------|
| 7     | Application  | Data                 |
| 6     | Presentation | Data                 |
| 5     | Session      | Data                 |
| 4     | Transport    | Segment / Datagram   |
| 3     | Network      | Packet               |
| 2     | Data Link    | Frame                |
| 1     | Physical     | Bits                 |

---

## Encapsulation and Decapsulation

### Encapsulation

When data is sent through a network, each layer adds information required by that layer. This process is called encapsulation. As the data moves downward through the OSI model, additional information is added.

```text
Data
  |
  v
Segment
  |
  v
Packet
  |
  v
Frame
  |
  v
Bits
```

### Decapsulation

When the receiving device receives the data, the process occurs in the opposite direction. This is called decapsulation.

```text
Bits
  |
  v
Frame
  |
  v
Packet
  |
  v
Segment
  |
  v
Data
```

Each layer processes the information relevant to itself and passes the remaining data to the next layer.

---

## Layer-to-Layer Communication

Each OSI layer has a specific responsibility. A simplified communication path:

```text
Sender                                  Receiver

Application  ------------------------> Application
Presentation ------------------------> Presentation
Session      ------------------------> Session
Transport    ------------------------> Transport
Network      ------------------------> Network
Data Link    ------------------------> Data Link
Physical     ========================> Physical
```

In an actual network, data passes through the layers on the sending device, travels across the network, and is then processed through the layers on the receiving device.

---

## OSI Model and Network Devices

Different network devices primarily operate at different layers.

| Device   | Common OSI Layer |
|----------|------------------|
| Hub      | Layer 1 |
| Switch   | Layer 2 |
| Bridge   | Layer 2 |
| Router   | Layer 3 |
| Firewall | Depends on its design and functionality |
| Gateway  | Can operate across multiple layers |

> **Note:** These associations are simplified, and modern devices can provide functions across multiple OSI layers.

---

## MAC Address and IP Address

### MAC Address

A MAC address is associated primarily with the Data Link layer. It is used for communication within the local network environment.

```text
Layer 2 -> MAC Address
```

### IP Address

An IP address is associated primarily with the Network layer. It is used for logical addressing and communication between networks.

```text
Layer 3 -> IP Address
```

---

## OSI Model and Troubleshooting

The OSI model can be used as a structured way to troubleshoot network problems. A basic approach is to start from the lower layers and move upward.

```text
Layer 1 - Physical connectivity
      |
      v
Layer 2 - Data Link / MAC / Ethernet
      |
      v
Layer 3 - IP / Routing
      |
      v
Layer 4 - TCP / UDP / Ports
      |
      v
Layer 7 - Application protocols
```

For example, if a computer has no network connection, physical connectivity should be considered before investigating higher-layer problems.

---

## Layer Summary

| Layer | Name         | Main Concepts |
|-------|--------------|---------------|
| 7     | Application  | Network services and application protocols |
| 6     | Presentation | Data representation, encryption, compression |
| 5     | Session      | Session management |
| 4     | Transport    | TCP, UDP, ports, end-to-end communication |
| 3     | Network      | IP, packets, routing |
| 2     | Data Link    | MAC, frames, Ethernet, switching |
| 1     | Physical     | Bits, cables, signals, physical media |

---

## Key Takeaways

- The OSI model has seven layers.
- Layer 1 is Physical, Layer 2 is Data Link, Layer 3 is Network, Layer 4 is Transport, Layer 5 is Session, Layer 6 is Presentation, and Layer 7 is Application.
- MAC addresses are primarily associated with Layer 2.
- IP addresses are primarily associated with Layer 3.
- TCP and UDP operate at Layer 4.
- Encapsulation occurs as data moves down the stack.
- Decapsulation occurs as data moves up the stack on the receiving side.
- The OSI model is useful for understanding and troubleshooting network communication.

---

## Practice

### Write the Seven OSI Layers

Write the seven OSI layers from Layer 1 to Layer 7.

### Identify the OSI Layer

Identify the OSI layer associated with each item:

- MAC Address
- IP Address
- TCP
- UDP
- Ethernet
- HTTP

### Identify the Data Unit

Identify the data unit at each layer:

- Physical
- Data Link
- Network
- Transport

### Encapsulation and Decapsulation

Describe the difference between encapsulation and decapsulation.

### Identify Device Layers

Identify the primary OSI layer associated with:

- Hub
- Switch
- Router

### Troubleshooting

Use the OSI model to describe a basic troubleshooting process from the Physical layer toward the Application layer.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
