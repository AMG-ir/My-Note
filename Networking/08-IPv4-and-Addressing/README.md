IPv4 and Addressing

IPv4 addressing is used to identify devices and interfaces on IP networks.

An IPv4 address is a 32-bit address divided into four 8-bit sections called octets.

IPv4 Address Format

An IPv4 address is normally written in dotted-decimal notation.

```
192.168.1.10
```

Each octet can have a value from:

```
0 - 255
```

An IPv4 address contains 32 bits:

```
8 bits + 8 bits + 8 bits + 8 bits = 32 bits
```

Example:

```
192.168.1.10
```

Binary representation:

```
11000000.10101000.00000001.00001010
```

---

IPv4 Address Classes

Traditional IPv4 addressing divides addresses into five classes:

· Class A
· Class B
· Class C
· Class D
· Class E

Class A

```
1 - 126
```

Default subnet mask:

```
255.0.0.0
```

Class A was designed for very large networks.

Example:

```
10.0.0.1
```

---

Class B

```
128 - 191
```

Default subnet mask:

```
255.255.0.0
```

Class B was designed for medium-sized networks.

Example:

```
172.16.0.1
```

---

Class C

```
192 - 223
```

Default subnet mask:

```
255.255.255.0
```

Class C was designed for smaller networks.

Example:

```
192.168.1.1
```

---

Class D

```
224 - 239
```

Class D addresses are used for multicast.

Example:

```
224.0.0.1
```

---

Class E

```
240 - 255
```

Class E addresses are reserved for experimental purposes.

---

IPv4 Class Comparison

Class First Octet Default Mask Main Use
A 1-126 255.0.0.0 Large networks
B 128-191 255.255.0.0 Medium networks
C 192-223 255.255.255.0 Smaller networks
D 224-239 N/A Multicast
E 240-255 N/A Experimental

The address 127.0.0.0/8 is reserved for loopback and is not part of the normal Class A host range.

---

Network and Host Portions

An IPv4 address can be divided into:

· Network portion
· Host portion

For example, with the traditional Class C default mask:

Address:

```
192.168.1.10
```

Mask:

```
255.255.255.0
```

The network portion is:

```
192.168.1
```

The host portion is:

```
10
```

---

Subnet Mask

A subnet mask determines which part of an IPv4 address represents the network and which part represents the host.

Example:

```
IP Address:   192.168.1.10
Subnet Mask:  255.255.255.0
```

The same mask can also be written using CIDR notation:

```
192.168.1.10/24
```

Here:

```
/24
```

means that the first 24 bits represent the network portion.

---

CIDR Notation

CIDR represents the network prefix using a slash followed by the number of network bits.

Examples:

```
192.168.1.0/24
10.0.0.0/8
172.16.0.0/16
```

Common prefixes:

CIDR Subnet Mask
/8 255.0.0.0
/16 255.255.0.0
/24 255.255.255.0

---

Private IPv4 Address Ranges

Private IPv4 addresses are used inside private networks.

Class A Private Range

```
10.0.0.0/8
```

Range:

```
10.0.0.0 - 10.255.255.255
```

Class B Private Range

```
172.16.0.0/12
```

Range:

```
172.16.0.0 - 172.31.255.255
```

Class C Private Range

```
192.168.0.0/16
```

Range:

```
192.168.0.0 - 192.168.255.255
```

---

Public and Private Addresses

Private IP

Used inside private networks.

Example:

```
192.168.1.20
```

Private addresses are not directly routable across the public Internet.

Public IP

A public IP address can be used for communication across the public Internet.

Example:

```
203.0.113.10
```

---

Special IPv4 Addresses

Loopback

The loopback range is:

```
127.0.0.0/8
```

A commonly used loopback address is:

```
127.0.0.1
```

It refers to the local host.

Unspecified Address

```
0.0.0.0
```

This can represent an unspecified address or, depending on context, all IPv4 interfaces or the default route.

Limited Broadcast

```
255.255.255.255
```

This represents a limited IPv4 broadcast.

---

Network Address

A network address identifies the network itself.

Example:

```
192.168.1.0/24
```

Here:

```
192.168.1.0
```

is the network address.

---

Broadcast Address

A broadcast address is used to send traffic to all hosts on a local IPv4 network.

For:

```
192.168.1.0/24
```

the broadcast address is:

```
192.168.1.255
```

---

Host Address

A host address identifies a device or network interface within a network.

Example:

```
192.168.1.10
```

For the network:

```
192.168.1.0/24
```

192.168.1.10 can be assigned to a host.

---

Default Gateway

A default gateway is the device a host uses to reach destinations outside its local network.

Example:

```
IP Address:
192.168.1.10

Subnet Mask:
255.255.255.0

Default Gateway:
192.168.1.1
```

Communication within the local network can occur directly.

For destinations outside the local network, traffic is normally sent toward the default gateway.

---

IPv4 Address Example

Consider:

```
IP Address:      192.168.1.50
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
```

The network is:

```
192.168.1.0/24
```

The host address is:

```
192.168.1.50
```

The broadcast address is:

```
192.168.1.255
```

---

IPv4 Addressing Summary

Concept Example
IPv4 Address 192.168.1.10
Subnet Mask 255.255.255.0
CIDR /24
Network Address 192.168.1.0
Host Address 192.168.1.10
Broadcast Address 192.168.1.255
Default Gateway 192.168.1.1

---

Key Takeaways

· IPv4 addresses are 32 bits long.
· IPv4 addresses are written using four decimal octets.
· Each octet ranges from 0 to 255.
· Traditional IPv4 classes are A, B, C, D, and E.
· Class D is used for multicast.
· Class E is reserved for experimental purposes.
· A subnet mask separates the network and host portions of an address.
· CIDR notation represents the network prefix length.
· Private IPv4 ranges are used inside private networks.
· A default gateway provides a path toward other networks.
· A network address identifies the network.
· A broadcast address is used to reach all hosts on a local IPv4 network.

---

Practice

1. How many bits are in an IPv4 address?
2. What is the range of values for each IPv4 octet?
3. Identify the class of each address:
   · 10.10.10.10
   · 172.16.1.1
   · 192.168.1.1
   · 224.0.0.1
4. What is the subnet mask for /24?
5. What is the private range 10.0.0.0/8 used for?
6. What is the purpose of 127.0.0.1?
7. For 192.168.1.0/24, identify:
   · Network address
   · Broadcast address
   · A valid host address
8. Explain the purpose of a default gateway.
