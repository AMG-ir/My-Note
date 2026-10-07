Network Protocols

Network protocols are rules and standards that define how devices communicate and exchange data across a network.

Protocols operate at different layers of the TCP/IP model and provide different functions such as addressing, routing, transport, name resolution, web communication, file transfer, email, and remote access.

---

1. Application Layer Protocols

Application layer protocols provide network services directly to applications and users.

HTTP

HTTP (Hypertext Transfer Protocol) is used for communication between web clients and web servers.

```text
Client ───── HTTP ─────> Web Server
```

Commonly associated with:

```
Port: 80
```

---

HTTPS

HTTPS is HTTP protected using TLS encryption.

```text
Client ───── HTTPS ─────> Web Server
```

Commonly associated with:

```
Port: 443
```

HTTPS provides encrypted communication between the client and server.

---

DNS

DNS (Domain Name System) translates domain names into IP addresses and provides name-resolution services.

Example:

```text
www.example.com
        |
        v
    DNS Server
        |
        v
   IP Address
```

Commonly associated with:

```
Port: 53
```

DNS can use both UDP and TCP depending on the type of communication.

---

DHCP

DHCP (Dynamic Host Configuration Protocol) automatically provides network configuration to clients.

A DHCP server can provide information such as:

· IP address
· Subnet mask
· Default gateway
· DNS server

A common DHCP process is:

```text
Discover
   ↓
Offer
   ↓
Request
   ↓
Acknowledge
```

DHCP commonly uses:

```text
UDP 67  - Server
UDP 68  - Client
```

---

FTP

FTP (File Transfer Protocol) is used for transferring files between systems.

```text
Client ───── FTP ─────> FTP Server
```

Commonly associated with:

```text
TCP 21 - Control
TCP 20 - Data
```

FTP does not provide encryption by itself.

---

SSH

SSH (Secure Shell) provides secure remote access to systems.

```text
Client ───── SSH ─────> Remote Server
```

Commonly associated with:

```text
TCP 22
```

SSH can be used for:

· Remote administration
· Secure command-line access
· Secure file-related operations

---

Telnet

Telnet provides remote terminal access.

Commonly associated with:

```text
TCP 23
```

Telnet does not encrypt the communication by default.

Because of this, SSH is generally preferred for secure remote administration.

---

SMTP

SMTP (Simple Mail Transfer Protocol) is used for sending and relaying email.

Common ports include:

```text
TCP 25
TCP 587
```

SMTP is primarily used for sending mail rather than retrieving it.

---

POP3

POP3 (Post Office Protocol version 3) is used to retrieve email from a mail server.

Commonly associated with:

```text
TCP 110
```

A secure version commonly uses:

```text
TCP 995
```

---

IMAP

IMAP (Internet Message Access Protocol) is used to access and manage email stored on a mail server.

Commonly associated with:

```text
TCP 143
```

A secure version commonly uses:

```text
TCP 993
```

---

2. Transport Layer Protocols

The main transport protocols are:

· TCP
· UDP

---

TCP

TCP (Transmission Control Protocol) provides connection-oriented and reliable communication.

TCP provides mechanisms for:

· Reliable delivery
· Ordered data
· Connection management
· Flow control

Basic communication:

```text
Client ───── TCP Connection ─────> Server
```

TCP uses a three-way handshake to establish a connection:

```text
Client                  Server

   SYN ------------------->
       <---------------- SYN-ACK
   ACK ------------------->
```

---

UDP

UDP (User Datagram Protocol) provides connectionless communication.

UDP has lower overhead than TCP but does not provide TCP-style reliability or ordering.

```text
Client ───── UDP Datagram ─────> Server
```

UDP is commonly used when low overhead or fast transmission is important.

---

TCP vs UDP

Feature TCP UDP
Connection Connection-oriented Connectionless
Reliability Yes No built-in reliability
Ordering Yes No
Overhead Higher Lower
Speed Generally slower Generally faster
Common Uses HTTP/HTTPS, SSH, FTP DNS, DHCP, streaming/real-time traffic

---

3. Network Layer Protocols

IP

IP (Internet Protocol) provides logical addressing and packet delivery between networks.

IPv4 example:

```text
192.168.1.10
```

Routers use IP information to make forwarding decisions.

---

ICMP

ICMP (Internet Control Message Protocol) is used for network control, diagnostics, and error reporting.

A common example is:

```bash
ping
```

Ping uses ICMP Echo Request and Echo Reply messages for IPv4.

```text
Host A ─── Echo Request ───> Host B
Host A <── Echo Reply ────── Host B
```

---

ARP

ARP (Address Resolution Protocol) is used in IPv4 networks to discover the MAC address associated with an IPv4 address on the local network.

Example:

```text
Who has 192.168.1.1?
```

The device with that IP can respond with its MAC address.

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

4. Ethernet

Ethernet is a widely used technology for wired local area networks.

Ethernet operates primarily at the Data Link and Physical layers.

Ethernet uses MAC addresses for communication within a local network.

Example:

```text
PC ───── Switch ───── PC
```

---

5. Network Protocol and Port

A port identifies a specific service or application endpoint on a host.

Examples:

Protocol Common Port Transport
HTTP 80 TCP
HTTPS 443 TCP
DNS 53 UDP/TCP
DHCP 67/68 UDP
FTP 20/21 TCP
SSH 22 TCP
Telnet 23 TCP
SMTP 25/587 TCP
POP3 110 TCP
IMAP 143 TCP

A port number combined with an IP address helps identify a network service.

Example:

```text
192.168.1.10:22
```

This represents a service reachable at TCP port 22 on that IP address.

---

6. Protocols by TCP/IP Layer

TCP/IP Layer Examples
Application HTTP, HTTPS, DNS, DHCP, FTP, SSH, Telnet, SMTP, POP3, IMAP
Transport TCP, UDP
Internet IP, ICMP, ARP
Network Access Ethernet

---

7. Secure vs Insecure Protocols

Some protocols provide encryption while others do not.

Secure Examples

· HTTPS
· SSH

Insecure Examples

· HTTP
· FTP
· Telnet

The security of a protocol depends on how communication is protected and configured.

---

Key Takeaways

· Network protocols define how devices communicate.
· HTTP and HTTPS are used for web communication.
· DNS provides name resolution.
· DHCP provides automatic network configuration.
· FTP is used for file transfer.
· SSH provides secure remote access.
· Telnet provides remote access without encryption by default.
· SMTP is used for sending email.
· POP3 and IMAP are used for email retrieval and access.
· TCP provides reliable, connection-oriented communication.
· UDP provides connectionless communication with lower overhead.
· IP provides logical addressing and packet delivery.
· ICMP is used for diagnostics and network control.
· ARP maps IPv4 addresses to MAC addresses on a local network.
· Ethernet is widely used for wired LAN communication.
· Port numbers identify network services on hosts.

---

Practice

1. What is the purpose of HTTP?
2. What is the difference between HTTP and HTTPS?
3. What is DNS used for?
4. What information can DHCP provide to a client?
5. What is the difference between TCP and UDP?
6. What is the purpose of ICMP?
7. What is ARP used for?
8. What is the difference between SSH and Telnet?
9. Match each protocol with its common purpose:
   · DNS
   · DHCP
   · HTTP
   · FTP
   · SSH
   · SMTP
10. Identify the TCP/IP layer associated with:
    · TCP
    · UDP
    · IP
    · HTTP
    · Ethernet
