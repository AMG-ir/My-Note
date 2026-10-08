# 12 - Network Segmentation

Network segmentation is the process of dividing a network into separate logical or physical segments. Segmentation can improve network organization, security, performance, and traffic control.

## Contents

- [Why Segment a Network](#why-segment-a-network)
- [Network Segments](#network-segments)
- [LAN Segmentation](#lan-segmentation)
- [Broadcast Domains](#broadcast-domains)
- [Collision Domains](#collision-domains)
- [Router-Based Segmentation](#router-based-segmentation)
- [DMZ](#dmz)
- [Firewall and Segmentation](#firewall-and-segmentation)
- [Security Benefits](#security-benefits)
- [Performance Benefits](#performance-benefits)
- [Segmentation Example](#segmentation-example)
- [Segmentation and Access Control](#segmentation-and-access-control)
- [Internet, DMZ, and Internal Network](#internet-dmz-and-internal-network)
- [Segmentation Comparison](#segmentation-comparison)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## Why Segment a Network

A large network can contain many different types of devices, for example:

- Employees
- Servers
- Guests
- Security devices
- Network infrastructure

Putting everything into one network can make management and security more difficult. Segmentation allows different groups of devices to be separated.

---

## Network Segments

A network segment is a portion of a larger network.

```text
             Router
                |
        +-------+-------+
        |       |       |
       LAN    Servers  Guests
```

Each segment can have different addressing, access, and security requirements.

---

## LAN Segmentation

A LAN can be divided into multiple network segments.

```text
                Router
                  |
             Main Network
                  |
        +---------+---------+
        |         |         |
     Users     Servers    Guests
```

This can make it easier to control communication between different groups.

---

## Broadcast Domains

A broadcast domain is the group of devices that receive a Layer 2 broadcast. Routers can separate broadcast domains.

```text
Broadcast Domain A
        |
      Router
        |
Broadcast Domain B
```

Broadcast traffic from one side does not normally cross a router into the other broadcast domain.

---

## Collision Domains

A collision domain is a network area in which simultaneous transmissions can potentially interfere with each other.

A hub creates a shared collision domain:

```text
PC1 --+
PC2 --+-- Hub
PC3 --+
```

With a switch, each switch port is typically a separate collision domain:

```text
PC1 --+
      |
    Switch
      |
PC2 --+
```

---

## Router-Based Segmentation

A router can connect different IP networks.

```text
192.168.10.0/24
        |
      Router
        |
192.168.20.0/24
```

The router separates the two networks and can make routing decisions between them.

---

## DMZ

DMZ stands for Demilitarized Zone. A DMZ is a network segment designed to isolate publicly accessible services from an internal network.

```text
                 Internet
                    |
                 Firewall
                    |
             +------+------+
             |             |
            DMZ        Internal LAN
             |
      Public Services
```

Servers that need to be reachable from outside the organization can be placed in a DMZ. Examples may include:

- Web servers
- Public-facing services

> **Note:** The exact architecture depends on the network design and security requirements.

---

## Firewall and Segmentation

A firewall can control traffic between network segments.

```text
Internet
   |
Firewall
   |
   +------ DMZ
   |
   +------ Internal Network
```

The firewall can apply rules to determine which traffic is allowed or blocked. Segmentation and firewall rules can work together to limit unnecessary communication between network areas.

---

## Security Benefits

Segmentation can reduce the impact of a security incident.

```text
Compromised Device
        |
     Segment A
        |
    Restricted
        |
     Segment B
```

If communication between segments is restricted, a compromised device may have fewer opportunities to communicate with other systems. Segmentation is therefore an important part of network security design.

---

## Performance Benefits

Segmentation can also help manage network traffic. Separating devices into different segments can reduce unnecessary broadcast traffic within each segment.

```text
Segment A          Segment B

PC1                 PC4
PC2                 PC5
PC3                 PC6
```

Traffic intended for one segment does not automatically need to reach every device in another segment.

---

## Segmentation Example

Consider an organization with users, servers, guest devices, and security cameras. A possible design:

```text
                    Firewall
                       |
                    Router
                       |
        +--------------+--------------+
        |              |              |
      Users          Servers        Guests
```

Security cameras could also be placed in a separate network segment:

```text
                    Router
                       |
        +--------------+--------------+
        |              |              |
      Users          Servers        Cameras
                                      |
                                    Guests
```

> **Note:** The actual design depends on the organization's requirements.

---

## Segmentation and Access Control

Segmentation does not automatically make a network secure. Traffic between segments still needs appropriate access control.

```text
Users  -------> Servers      (Allowed)

Guests ---X---> Internal Servers      (Blocked)
```

A firewall or router can enforce rules between different networks.

---

## Internet, DMZ, and Internal Network

A common security architecture separates the external network, DMZ, and internal network.

```text
Internet
   |
Firewall
   |
  DMZ
   |
Firewall
   |
Internal LAN
```

The DMZ acts as an intermediate network between the public Internet and the internal network.

---

## Segmentation Comparison

| Concept          | Main Purpose |
|------------------|--------------|
| Network Segment  | Separates part of a network |
| Broadcast Domain | Defines where Layer 2 broadcasts are received |
| Collision Domain | Defines an area where collisions can occur |
| Router           | Connects different IP networks |
| Firewall         | Controls traffic between networks |
| DMZ              | Isolates public-facing services |

---

## Key Takeaways

- Network segmentation divides a network into separate areas.
- Segmentation can improve organization, security, and traffic management.
- Routers can separate different IP networks.
- Routers separate broadcast domains.
- Switch ports normally represent separate collision domains.
- A DMZ can isolate public-facing services from an internal network.
- Firewalls can control communication between network segments.
- Segmentation alone does not provide complete security.
- Appropriate access-control rules are required between segments.

---

## Practice

- What is network segmentation?
- Why might an organization divide its network into multiple segments?
- What is a broadcast domain?
- What is a collision domain?
- How can a router separate network segments?
- What is a DMZ?
- Why might public-facing servers be placed in a DMZ?
- How can a firewall control communication between segments?
- Explain one security benefit of network segmentation.
- Explain the difference between a broadcast domain and a collision domain.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
