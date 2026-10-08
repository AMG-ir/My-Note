# 03 - TCP/IP Model

The TCP/IP model is a networking model used to describe how devices communicate across networks.

## Overview

It is the foundation of modern Internet communication and organizes networking functions into four main layers.

## Contents

- [The Four TCP/IP Layers](#the-four-tcpip-layers)
- [Network Access Layer](#network-access-layer)
- [Internet Layer](#internet-layer)
- [Transport Layer](#transport-layer)
- [Application Layer](#application-layer)
- [TCP/IP and OSI Comparison](#tcpip-and-osi-comparison)
- [Protocols and Layers](#protocols-and-layers)
- [Encapsulation and Decapsulation](#encapsulation-and-decapsulation)
- [Communication Example](#communication-example)
- [TCP/IP Addressing](#tcpip-addressing)
- [TCP/IP Model and Network Devices](#tcpip-model-and-network-devices)
- [TCP vs UDP](#tcp-vs-udp)
- [Troubleshooting with the TCP/IP Model](#troubleshooting-with-the-tcpip-model)
- [Layer Summary](#layer-summary)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## The Four TCP/IP Layers

From the highest layer to the lowest:

```text
Layer 4 - Application
Layer 3 - Transport
Layer 2 - Internet
Layer 1 - Network Access
```

---

## Network Access Layer

The Network Access layer is responsible for communication over the local network and the physical transmission of data. It combines functions associated with the Physical and Data Link layers of the OSI model.

Important concepts include:

- Ethernet
- MAC addresses
- Network interfaces
- Frames
- Physical transmission
- Local network communication

```text
Data
  |
  v
Frame
  |
  v
Physical Transmission
```

---

## Internet Layer

The Internet layer is responsible for logical addressing and routing packets between networks.

Important concepts include:

- IP
- IPv4
- Packets
- Routing
- Routers

The Internet layer determines how packets move from one network to another. IP is the main protocol associated with this layer.

```text
Source Network
      |
    Router
      |
Destination Network
```

---

## Transport Layer

The Transport layer provides communication between applications running on networked devices. The main protocols are TCP and UDP.

### TCP

TCP provides reliable, connection-oriented communication. It provides mechanisms for:

- Reliable delivery
- Ordered data transfer
- Error detection
- Flow control
- Connection management

### UDP

UDP provides connectionless communication. Compared with TCP, UDP has less protocol overhead and does not provide the same reliability mechanisms as TCP.

---

## Application Layer

The Application layer provides network services used by applications. It combines the functions of the Application, Presentation, and Session layers of the OSI model.

Protocols commonly associated with this layer include:

- HTTP
- HTTPS
- FTP
- SSH
- DNS
- DHCP
- SMTP
- POP3
- IMAP
- Telnet

---

## TCP/IP and OSI Comparison

The TCP/IP model has four layers, while the OSI model has seven. The layers can be mapped approximately as follows:

| TCP/IP Model   | OSI Model |
|----------------|-----------|
| Application    | Application, Presentation, Session |
| Transport      | Transport |
| Internet       | Network |
| Network Access | Data Link, Physical |

The TCP/IP Application layer combines the functionality of three OSI layers. The TCP/IP Network Access layer combines the functionality of two OSI layers.

```text
OSI                      TCP/IP
7 - Application          4 - Application
6 - Presentation
5 - Session
4 - Transport            3 - Transport
3 - Network              2 - Internet
2 - Data Link            1 - Network Access
1 - Physical
```

The OSI model is mainly used as a conceptual reference model, while TCP/IP represents the architecture used by modern Internet networking.

---

## Protocols and Layers

| TCP/IP Layer   | Examples |
|----------------|----------|
| Application    | HTTP, HTTPS, FTP, SSH, DNS, DHCP, SMTP, POP3, IMAP, Telnet |
| Transport      | TCP, UDP |
| Internet       | IP, ICMP |
| Network Access | Ethernet, ARP |

> **Note:** The exact implementation of some technologies can involve functionality across more than one layer, but this table provides a basic model for understanding their roles.

---

## Encapsulation and Decapsulation

### Encapsulation

When an application sends data, the data moves down through the TCP/IP layers. Each layer adds information needed for communication.

```text
Application Data
       |
       v
Transport
       |
       v
Internet
       |
       v
Network Access
       |
       v
Physical Network
```

The resulting data units:

```text
Data
  |
  v
Segment / Datagram
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

At the receiving device, the process occurs in reverse.

```text
Physical Network
       |
       v
Network Access
       |
       v
Internet
       |
       v
Transport
       |
       v
Application
```

The receiving system processes the information associated with each layer and eventually delivers the data to the appropriate application.

---

## Communication Example

Consider a client accessing a web server.

```text
Client
  |
  | HTTP/HTTPS
  v
Application Layer
  |
  | TCP
  v
Transport Layer
  |
  | IP
  v
Internet Layer
  |
  | Ethernet / Wireless
  v
Network Access
  |
  v
Network
  |
  v
Server
```

The server processes the received information through the corresponding layers.

---

## TCP/IP Addressing

Different layers use different identifiers during communication.

| Identifier  | Layer          | Purpose |
|-------------|----------------|---------|
| MAC address | Network Access | Local network communication |
| IP address  | Internet       | Logical addressing between networks |
| Port        | Transport      | Identifies the application or service involved in communication |

---

## TCP/IP Model and Network Devices

Different devices operate primarily at different layers, although modern devices can perform functions across multiple layers.

| Device   | Primary Role |
|----------|--------------|
| Hub      | Physical transmission |
| Switch   | Local network communication |
| Router   | Routing between networks |
| Gateway  | Communication between different networks or systems |
| Firewall | Traffic control and security |

---

## TCP vs UDP

| Feature       | TCP                     | UDP |
|---------------|-------------------------|-----|
| Connection    | Connection-oriented     | Connectionless |
| Reliability   | Reliable                | No built-in reliability like TCP |
| Ordering      | Maintains ordered delivery | Does not guarantee ordered delivery |
| Overhead      | Higher                  | Lower |
| Main purpose  | Reliable communication  | Lightweight communication |

The choice between TCP and UDP depends on the requirements of the application.

---

## Troubleshooting with the TCP/IP Model

The TCP/IP model can also help organize network troubleshooting.

```text
Network Access
      |
      v
Internet
      |
      v
Transport
      |
      v
Application
```

For example:

- Check local network connectivity at the Network Access layer.
- Check IP addressing and routing at the Internet layer.
- Check TCP/UDP and ports at the Transport layer.
- Check the relevant network service at the Application layer.

---

## Layer Summary

| Layer          | Main Function                          | Examples |
|----------------|----------------------------------------|----------|
| Application    | Network services for applications      | HTTP, DNS, SSH, FTP |
| Transport      | End-to-end communication               | TCP, UDP |
| Internet       | Logical addressing and routing         | IP, ICMP |
| Network Access | Local network and physical communication | Ethernet, ARP |

---

## Key Takeaways

- The TCP/IP model has four main layers.
- The Application layer provides network services to applications.
- The Transport layer provides end-to-end communication using TCP or UDP.
- The Internet layer handles IP addressing and routing.
- The Network Access layer handles local network and physical communication.
- TCP provides reliable, connection-oriented communication.
- UDP provides connectionless communication with lower overhead.
- IP addresses are associated with the Internet layer.
- MAC addresses are primarily associated with the Network Access layer.
- Ports are associated with the Transport layer.
- Encapsulation occurs as data moves down the model.
- Decapsulation occurs as data moves up the model on the receiving system.

---

## Practice

### Write the Four TCP/IP Layers

Write the four TCP/IP layers from lowest to highest.

### Identify the TCP/IP Layer

Identify the TCP/IP layer associated with each:

- TCP
- UDP
- IP
- Ethernet
- HTTP

### TCP and UDP

Explain the main difference between TCP and UDP.

### Map TCP/IP to OSI

Map the TCP/IP layers to the seven OSI layers.

### Identify Addressing Layers

Identify the layer associated with:

- MAC Address
- IP Address
- Port

### Describe a Data Path

Describe the path of data when a client communicates with a remote server using the TCP/IP model.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
