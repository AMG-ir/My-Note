# 06 - IPv4 and Subnetting

This section documents IPv4 addressing and subnetting concepts studied during Cisco networking training.

## Contents

- [IPv4 Address](#ipv4-address)
- [Subnet Mask](#subnet-mask)
- [IPv4 Address Classes](#ipv4-address-classes)
- [Private IPv4 Address Ranges](#private-ipv4-address-ranges)
- [Network and Broadcast Addresses](#network-and-broadcast-addresses)
- [Default Gateway](#default-gateway)
- [Subnetting](#subnetting)
- [Key Takeaways](#key-takeaways)

---

## IPv4 Address

An IPv4 address is a 32-bit address represented as four decimal octets separated by dots.

```text
192.168.1.10
```

Each octet has a value from 0 to 255.

---

## Subnet Mask

A subnet mask identifies the network portion and host portion of an IPv4 address.

```text
IP Address:  192.168.1.10
Subnet Mask: 255.255.255.0
CIDR Prefix: /24
```

In this example, the first 24 bits represent the network portion.

---

## IPv4 Address Classes

Traditional IPv4 classful addressing defines five address classes.

| Class | First Octet Range | Traditional Default Mask |
|-------|-------------------|--------------------------|
| A     | 1-126             | `255.0.0.0` (/8) |
| B     | 128-191           | `255.255.0.0` (/16) |
| C     | 192-223           | `255.255.255.0` (/24) |
| D     | 224-239           | Not used for ordinary unicast host addressing |
| E     | 240-255           | Reserved |

> **Note:** Classful addressing is a historical model. Modern IP networks generally use CIDR and prefix lengths.

---

## Private IPv4 Address Ranges

The following IPv4 ranges are reserved for private networks.

| Range                          | CIDR |
|--------------------------------|------|
| 10.0.0.0 - 10.255.255.255      | `10.0.0.0/8` |
| 172.16.0.0 - 172.31.255.255    | `172.16.0.0/12` |
| 192.168.0.0 - 192.168.255.255  | `192.168.0.0/16` |

Private addresses are commonly used in local networks.

---

## Network and Broadcast Addresses

In a typical IPv4 subnet:

- Network address: identifies the subnet.
- Broadcast address: identifies all hosts on the subnet.
- Host address: an address assigned to an interface within the subnet.

For example, in `192.168.1.0/24`:

| Type         | Address |
|--------------|---------|
| Network      | `192.168.1.0` |
| Example Host | `192.168.1.10` |
| Broadcast    | `192.168.1.255` |

---

## Default Gateway

A default gateway is the router or Layer 3 device that a host uses to reach destinations outside its local subnet when no more specific route applies.

```text
IP Address:      192.168.1.10
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
```

---

## Subnetting

Subnetting divides an IP network into smaller networks. To work out a subnetting question, identify:

1. The original network address.
2. The required subnet mask or prefix length.
3. The resulting network and broadcast addresses.
4. The usable host address range, where applicable.

---

## Key Takeaways

- IPv4 addresses contain 32 bits.
- Subnet masks and CIDR prefixes identify network boundaries.
- Private IPv4 ranges are commonly used in LANs.
- Routers forward traffic between IP networks.
- Subnetting divides a network into smaller subnets.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
