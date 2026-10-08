# 09 - Network Protocols

Network protocols are rules and standards that define how devices communicate and exchange data across a network.

## Overview

Protocols operate at different layers of the TCP/IP model and provide different functions such as addressing, routing, transport, name resolution, web communication, file transfer, email, and remote access.

## Contents

- [Application Layer Protocols](#application-layer-protocols)
- [Transport Layer Protocols](#transport-layer-protocols)
- [Network Layer Protocols](#network-layer-protocols)
- [Ethernet](#ethernet)
- [Protocols and Ports](#protocols-and-ports)
- [Protocols by TCP/IP Layer](#protocols-by-tcpip-layer)
- [Secure vs Insecure Protocols](#secure-vs-insecure-protocols)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## Application Layer Protocols

Application layer protocols provide network services directly to applications and users.

### HTTP

HTTP (Hypertext Transfer Protocol) is used for communication between web clients and web servers. Commonly associated with port 80.

```text
Client ----- HTTP -----> Web Server
```

### HTTPS

HTTPS is HTTP protected using TLS encryption. Commonly associated with port 443. It provides encrypted communication between the client and server.

```text
Client ----- HTTPS -----> Web Server
```

### DNS

DNS (Domain Name System) translates domain names into IP addresses and provides name-resolution services. Commonly associated with port 53. DNS can use both UDP and TCP depending on the type of communication.

```text
www.example.com
        |
        v
    DNS Server
        |
        v
   IP Address
```

### DHCP

DHCP (Dynamic Host Configuration Protocol) automatically provides network configuration to clients. A DHCP server can provide:

- IP address
- Subnet mask
- Default gateway
- DNS server

A common DHCP process:

```text
Discover
   |
   v
Offer
   |
   v
Request
   |
   v
Acknowledge
```

DHCP commonly uses UDP 67 (server) and UDP 68 (client).

### FTP

FTP (File Transfer Protocol) is used for transferring files between systems. Commonly associated with TCP 21 (control) and TCP 20 (data).

```text
Client ----- FTP -----> FTP Server
```

> **Note:** FTP does not provide encryption by itself.

### SSH

SSH (Secure Shell) provides secure remote access to systems. Commonly associated with TCP 22.

```text
Client ----- SSH -----> Remote Server
```

SSH can be used for:

- Remote administration
- Secure command-line access
- Secure file-related operations

### Telnet

Telnet provides remote terminal access. Commonly associated with TCP 23.

> **Note:** Telnet does not encrypt the communication by default. Because of this, SSH is generally preferred for secure remote administration.

### SMTP

SMTP (Simple Mail Transfer Protocol) is used for sending and relaying email. Common ports are TCP 25 and TCP 587. SMTP is primarily used for sending mail rather than retrieving it.

### POP3

POP3 (Post Office Protocol version 3) is used to retrieve email from a mail server. Commonly associated with TCP 110. A secure version commonly uses TCP 995.

### IMAP

IMAP (Internet Message Access Protocol) is used to access and manage email stored on a mail server. Commonly associated with TCP 143. A secure version commonly uses TCP 993.

---

## Transport Layer Protocols

The main transport protocols are TCP and UDP.

### TCP

TCP (Transmission Control Protocol) provides connection-oriented and reliable communication. It provides mechanisms for:

- Reliable delivery
- Ordered data
- Connection management
- Flow control

TCP uses a three-way handshake to establish a connection:

```text
Client                  Server

   SYN ------------------->
       <---------------- SYN-ACK
   ACK ------------------->
```

### UDP

UDP (User Datagram Protocol) provides connectionless communication. UDP has lower overhead than TCP but does not provide TCP-style reliability or ordering. It is commonly used when low overhead or fast transmission is important.

```text
Client ----- UDP Datagram -----> Server
```

### TCP vs UDP

| Feature     | TCP                         | UDP |
|-------------|-----------------------------|-----|
| Connection  | Connection-oriented         | Connectionless |
| Reliability | Yes                         | No built-in reliability |
| Ordering    | Yes                         | No |
| Overhead    | Higher                      | Lower |
| Speed       | Generally slower            | Generally faster |
| Common Uses | HTTP/HTTPS, SSH, FTP        | DNS, DHCP, streaming/real-time traffic |

---

## Network Layer Protocols

### IP

IP (Internet Protocol) provides logical addressing and packet delivery between networks. Routers use IP information to make forwarding decisions.

### ICMP

ICMP (Internet Control Message Protocol) is used for network control, diagnostics, and error reporting. A common example is `ping`, which uses ICMP Echo Request and Echo Reply messages for IPv4.

```text
Host A --- Echo Request ---> Host B
Host A <-- Echo Reply ------ Host B
```

### ARP

ARP (Address Resolution Protocol) is used in IPv4 networks to discover the MAC address associated with an IPv4 address on the local network. For example, a device asks "Who has 192.168.1.1?" and the device with that IP can respond with its MAC address.

```text
IPv4 Address
     |
     v
    ARP
     |
     v
MAC Address
```

---

## Ethernet

Ethernet is a widely used technology for wired local area networks. It operates primarily at the Data Link and Physical layers and uses MAC addresses for communication within a local network.

```text
PC ----- Switch ----- PC
```

---

## Protocols and Ports

A port identifies a specific service or application endpoint on a host.

| Protocol | Common Port | Transport |
|----------|-------------|-----------|
| HTTP     | 80          | TCP |
| HTTPS    | 443         | TCP |
| DNS      | 53          | UDP/TCP |
| DHCP     | 67/68       | UDP |
| FTP      | 20/21       | TCP |
| SSH      | 22          | TCP |
| Telnet   | 23          | TCP |
| SMTP     | 25/587      | TCP |
| POP3     | 110         | TCP |
| IMAP     | 143         | TCP |

A port number combined with an IP address helps identify a network service. For example, `192.168.1.10:22` represents a service reachable at TCP port 22 on that IP address.

---

## Protocols by TCP/IP Layer

| TCP/IP Layer   | Examples |
|----------------|----------|
| Application    | HTTP, HTTPS, DNS, DHCP, FTP, SSH, Telnet, SMTP, POP3, IMAP |
| Transport      | TCP, UDP |
| Internet       | IP, ICMP, ARP |
| Network Access | Ethernet |

---

## Secure vs Insecure Protocols

Some protocols provide encryption while others do not.

- Secure examples: HTTPS, SSH
- Insecure examples: HTTP, FTP, Telnet

> **Note:** The security of a protocol depends on how communication is protected and configured.

---

## Key Takeaways

- Network protocols define how devices communicate.
- HTTP and HTTPS are used for web communication.
- DNS provides name resolution.
- DHCP provides automatic network configuration.
- FTP is used for file transfer.
- SSH provides secure remote access.
- Telnet provides remote access without encryption by default.
- SMTP is used for sending email.
- POP3 and IMAP are used for email retrieval and access.
- TCP provides reliable, connection-oriented communication.
- UDP provides connectionless communication with lower overhead.
- IP provides logical addressing and packet delivery.
- ICMP is used for diagnostics and network control.
- ARP maps IPv4 addresses to MAC addresses on a local network.
- Ethernet is widely used for wired LAN communication.
- Port numbers identify network services on hosts.

---

## Practice

- What is the purpose of HTTP?
- What is the difference between HTTP and HTTPS?
- What is DNS used for?
- What information can DHCP provide to a client?
- What is the difference between TCP and UDP?
- What is the purpose of ICMP?
- What is ARP used for?
- What is the difference between SSH and Telnet?
- Match each protocol (DNS, DHCP, HTTP, FTP, SSH, SMTP) with its common purpose.
- Identify the TCP/IP layer associated with TCP, UDP, IP, HTTP, and Ethernet.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
