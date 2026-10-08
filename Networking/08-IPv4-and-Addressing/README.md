# 08 - IPv4 and Addressing

IPv4 addressing is used to identify devices and interfaces on IP networks.

## Overview

An IPv4 address is a 32-bit address divided into four 8-bit sections called octets.

## Contents

- [IPv4 Address Format](#ipv4-address-format)
- [IPv4 Address Classes](#ipv4-address-classes)
- [Network and Host Portions](#network-and-host-portions)
- [Subnet Mask](#subnet-mask)
- [CIDR Notation](#cidr-notation)
- [Private IPv4 Address Ranges](#private-ipv4-address-ranges)
- [Public and Private Addresses](#public-and-private-addresses)
- [Special IPv4 Addresses](#special-ipv4-addresses)
- [Network, Broadcast, and Host Addresses](#network-broadcast-and-host-addresses)
- [Default Gateway](#default-gateway)
- [IPv4 Address Example](#ipv4-address-example)
- [IPv4 Addressing Summary](#ipv4-addressing-summary)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## IPv4 Address Format

An IPv4 address is normally written in dotted-decimal notation.

```text
192.168.1.10
```

Each octet can have a value from 0 to 255. An IPv4 address contains 32 bits:

```text
8 bits + 8 bits + 8 bits + 8 bits = 32 bits
```

Binary representation of `192.168.1.10`:

```text
11000000.10101000.00000001.00001010
```

---

## IPv4 Address Classes

Traditional IPv4 addressing divides addresses into five classes: A, B, C, D, and E.

| Class | First Octet | Default Mask    | Main Use | Example |
|-------|-------------|-----------------|----------|---------|
| A     | 1-126       | `255.0.0.0`     | Very large networks | `10.0.0.1` |
| B     | 128-191     | `255.255.0.0`   | Medium-sized networks | `172.16.0.1` |
| C     | 192-223     | `255.255.255.0` | Smaller networks | `192.168.1.1` |
| D     | 224-239     | N/A             | Multicast | `224.0.0.1` |
| E     | 240-255     | N/A             | Experimental | |

> **Note:** The address range `127.0.0.0/8` is reserved for loopback and is not part of the normal Class A host range.

---

## Network and Host Portions

An IPv4 address can be divided into a network portion and a host portion. For example, with the traditional Class C default mask:

```text
Address: 192.168.1.10
Mask:    255.255.255.0
```

The network portion is `192.168.1` and the host portion is `10`.

---

## Subnet Mask

A subnet mask determines which part of an IPv4 address represents the network and which part represents the host.

```text
IP Address:   192.168.1.10
Subnet Mask:  255.255.255.0
```

The same mask can also be written using CIDR notation:

```text
192.168.1.10/24
```

Here, `/24` means that the first 24 bits represent the network portion.

---

## CIDR Notation

CIDR represents the network prefix using a slash followed by the number of network bits.

```text
192.168.1.0/24
10.0.0.0/8
172.16.0.0/16
```

Common prefixes:

| CIDR  | Subnet Mask     |
|-------|-----------------|
| `/8`  | `255.0.0.0`     |
| `/16` | `255.255.0.0`   |
| `/24` | `255.255.255.0` |

---

## Private IPv4 Address Ranges

Private IPv4 addresses are used inside private networks.

| Class | CIDR              | Range |
|-------|-------------------|-------|
| A     | `10.0.0.0/8`      | `10.0.0.0 - 10.255.255.255` |
| B     | `172.16.0.0/12`   | `172.16.0.0 - 172.31.255.255` |
| C     | `192.168.0.0/16`  | `192.168.0.0 - 192.168.255.255` |

---

## Public and Private Addresses

**Private IP**

Used inside private networks, for example `192.168.1.20`. Private addresses are not directly routable across the public Internet.

**Public IP**

A public IP address can be used for communication across the public Internet, for example `203.0.113.10`.

---

## Special IPv4 Addresses

| Address            | Meaning |
|--------------------|---------|
| `127.0.0.0/8`      | Loopback range. `127.0.0.1` is commonly used and refers to the local host. |
| `0.0.0.0`          | Unspecified address. Depending on context, it can represent all IPv4 interfaces or the default route. |
| `255.255.255.255`  | Limited broadcast |

---

## Network, Broadcast, and Host Addresses

### Network Address

A network address identifies the network itself. For `192.168.1.0/24`, the network address is `192.168.1.0`.

### Broadcast Address

A broadcast address is used to send traffic to all hosts on a local IPv4 network. For `192.168.1.0/24`, the broadcast address is `192.168.1.255`.

### Host Address

A host address identifies a device or network interface within a network. For the network `192.168.1.0/24`, `192.168.1.10` can be assigned to a host.

---

## Default Gateway

A default gateway is the device a host uses to reach destinations outside its local network.

```text
IP Address:      192.168.1.10
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
```

Communication within the local network can occur directly. For destinations outside the local network, traffic is normally sent toward the default gateway.

---

## IPv4 Address Example

```text
IP Address:      192.168.1.50
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
```

- Network: `192.168.1.0/24`
- Host address: `192.168.1.50`
- Broadcast address: `192.168.1.255`

---

## IPv4 Addressing Summary

| Concept           | Example |
|-------------------|---------|
| IPv4 Address      | `192.168.1.10` |
| Subnet Mask       | `255.255.255.0` |
| CIDR              | `/24` |
| Network Address   | `192.168.1.0` |
| Host Address      | `192.168.1.10` |
| Broadcast Address | `192.168.1.255` |
| Default Gateway   | `192.168.1.1` |

---

## Key Takeaways

- IPv4 addresses are 32 bits long.
- IPv4 addresses are written using four decimal octets.
- Each octet ranges from 0 to 255.
- Traditional IPv4 classes are A, B, C, D, and E.
- Class D is used for multicast.
- Class E is reserved for experimental purposes.
- A subnet mask separates the network and host portions of an address.
- CIDR notation represents the network prefix length.
- Private IPv4 ranges are used inside private networks.
- A default gateway provides a path toward other networks.
- A network address identifies the network.
- A broadcast address is used to reach all hosts on a local IPv4 network.

---

## Practice

- How many bits are in an IPv4 address?
- What is the range of values for each IPv4 octet?
- Identify the class of each address: `10.10.10.10`, `172.16.1.1`, `192.168.1.1`, `224.0.0.1`.
- What is the subnet mask for `/24`?
- What is the private range `10.0.0.0/8` used for?
- What is the purpose of `127.0.0.1`?
- For `192.168.1.0/24`, identify the network address, the broadcast address, and a valid host address.
- Explain the purpose of a default gateway.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
