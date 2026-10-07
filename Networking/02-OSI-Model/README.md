OSI Model

The OSI (Open Systems Interconnection) model is a conceptual reference model used to understand how network communication works.

It divides network communication into seven layers. Each layer has a specific role and works with the layers above and below it.

1. The Seven OSI Layers

From the lowest layer to the highest:

```text
Layer 7 - Application
Layer 6 - Presentation
Layer 5 - Session
Layer 4 - Transport
Layer 3 - Network
Layer 2 - Data Link
Layer 1 - Physical
```

A common way to remember the order is:

```
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

---

2. Layer 1 - Physical

The Physical layer is responsible for the transmission of raw bits over a physical medium.

It deals with the physical characteristics of network communication.

Examples include:

· Cables
· Connectors
· Radio signals
· Electrical signals
· Optical signals
· Physical transmission media

The Physical layer does not understand IP addresses or application data. It deals with the transmission of bits.

```text
Bits → Physical Medium → Bits
```

---

3. Layer 2 - Data Link

The Data Link layer provides communication between devices on the same network segment.

Important concepts include:

· MAC addresses
· Frames
· Ethernet
· Switches
· Error detection
· Local network communication

The Data Link layer works with frames.

A simplified representation:

```text
Data → Frame → Data
```

MAC addresses are primarily associated with Layer 2.

---

4. Layer 3 - Network

The Network layer is responsible for logical addressing and routing between networks.

Important concepts include:

· IP addresses
· Routing
· Packets
· Routers
· Network-to-network communication

The Network layer works with packets.

```text
Data → Packet → Data
```

IP is a major protocol associated with this layer.

---

5. Layer 4 - Transport

The Transport layer provides end-to-end communication between applications.

Important concepts include:

· TCP
· UDP
· Ports
· Segmentation
· Reliability
· Flow control

TCP and UDP operate at the Transport layer.

TCP provides reliable, connection-oriented communication.

UDP provides connectionless communication with lower protocol overhead.

The Transport layer works with segments when using TCP and commonly with datagrams when using UDP.

---

6. Layer 5 - Session

The Session layer manages communication sessions between applications.

Its responsibilities can include:

· Establishing sessions
· Managing sessions
· Maintaining sessions
· Terminating sessions

The purpose of this layer is to organize and manage communication sessions between applications.

---

7. Layer 6 - Presentation

The Presentation layer deals with how data is represented.

Its responsibilities can include:

· Data formatting
· Data translation
· Encryption and decryption
· Compression and decompression

The layer helps ensure that data can be interpreted correctly by the receiving system.

---

8. Layer 7 - Application

The Application layer is the layer closest to the user and provides network services to applications.

Examples of protocols associated with the Application layer include:

· HTTP
· HTTPS
· FTP
· SSH
· DNS
· SMTP
· POP3
· IMAP

The Application layer does not mean the application itself. It provides network functionality used by applications.

---

9. OSI Layers and Data Units

Different layers use different terms to describe the data being handled.

```text
Layer 7 - Application   → Data
Layer 6 - Presentation  → Data
Layer 5 - Session       → Data
Layer 4 - Transport     → Segment / Datagram
Layer 3 - Network       → Packet
Layer 2 - Data Link     → Frame
Layer 1 - Physical      → Bits
```

This terminology is useful when analyzing network communication.

---

10. Encapsulation

When data is sent through a network, each layer adds information required by that layer.

This process is called encapsulation.

A simplified representation:

```text
Application Data
       ↓
Transport
       ↓
Network
       ↓
Data Link
       ↓
Physical
```

As the data moves downward through the OSI model, additional information is added.

For example:

```text
Data
  ↓
Segment
  ↓
Packet
  ↓
Frame
  ↓
Bits
```

---

11. Decapsulation

When the receiving device receives the data, the process occurs in the opposite direction.

This is called decapsulation.

```text
Bits
  ↓
Frame
  ↓
Packet
  ↓
Segment
  ↓
Data
```

Each layer processes the information relevant to itself and passes the remaining data to the next layer.

---

12. Layer-to-Layer Communication

Each OSI layer has a specific responsibility.

A simplified communication path:

```text
Sender                                  Receiver

Application  ────────────────────────> Application
Presentation ────────────────────────> Presentation
Session      ────────────────────────> Session
Transport    ────────────────────────> Transport
Network      ────────────────────────> Network
Data Link    ────────────────────────> Data Link
Physical     ════════════════════════> Physical
```

In an actual network, data passes through the layers on the sending device, travels across the network, and is then processed through the layers on the receiving device.

---

13. OSI Model and Network Devices

Different network devices primarily operate at different layers.

Device Common OSI Layer
Hub Layer 1
Switch Layer 2
Bridge Layer 2
Router Layer 3
Firewall Depends on its design and functionality
Gateway Can operate across multiple layers

These associations are simplified and modern devices can provide functions across multiple OSI layers.

---

14. MAC Address and IP Address

Two important addressing concepts are:

MAC Address

A MAC address is associated primarily with the Data Link layer.

```text
Layer 2 → MAC Address
```

It is used for communication within the local network environment.

IP Address

An IP address is associated primarily with the Network layer.

```text
Layer 3 → IP Address
```

It is used for logical addressing and communication between networks.

---

15. OSI Model and Troubleshooting

The OSI model can be used as a structured way to troubleshoot network problems.

A basic approach is to start from the lower layers and move upward.

```text
Layer 1
Physical connectivity
      ↓
Layer 2
Data Link / MAC / Ethernet
      ↓
Layer 3
IP / Routing
      ↓
Layer 4
TCP / UDP / Ports
      ↓
Layer 7
Application protocols
```

For example, if a computer has no network connection, physical connectivity should be considered before investigating higher-layer problems.

---

16. Layer Summary

Layer Name Main Concepts
7 Application Network services and application protocols
6 Presentation Data representation, encryption, compression
5 Session Session management
4 Transport TCP, UDP, ports, end-to-end communication
3 Network IP, packets, routing
2 Data Link MAC, frames, Ethernet, switching
1 Physical Bits, cables, signals, physical media

---

Key Takeaways

· The OSI model has seven layers.
· Layer 1 is the Physical layer.
· Layer 2 is the Data Link layer.
· Layer 3 is the Network layer.
· Layer 4 is the Transport layer.
· Layer 5 is the Session layer.
· Layer 6 is the Presentation layer.
· Layer 7 is the Application layer.
· MAC addresses are primarily associated with Layer 2.
· IP addresses are primarily associated with Layer 3.
· TCP and UDP operate at Layer 4.
· Encapsulation occurs as data moves down the stack.
· Decapsulation occurs as data moves up the stack on the receiving side.
· The OSI model is useful for understanding and troubleshooting network communication.

---

Practice

Practice 1

Write the seven OSI layers from Layer 1 to Layer 7.

Practice 2

Identify the OSI layer associated with each item:

· MAC Address
· IP Address
· TCP
· UDP
· Ethernet
· HTTP

Practice 3

Identify the data unit at each layer:

· Physical
· Data Link
· Network
· Transport

Practice 4

Describe the difference between encapsulation and decapsulation.

Practice 5

Identify the primary OSI layer associated with:

· Hub
· Switch
· Router

Practice 6

Use the OSI model to describe a basic troubleshooting process from the Physical layer toward the Application layer.
