Network Segmentation

Network segmentation is the process of dividing a network into separate logical or physical segments.

Segmentation can improve network organization, security, performance, and traffic control.

---

1. Why Segment a Network?

A large network can contain many different types of devices.

For example:

· Employees
· Servers
· Guests
· Security Devices
· Network Infrastructure

Putting everything into one network can make management and security more difficult.

Segmentation allows different groups of devices to be separated.

---

2. Network Segments

A network segment is a portion of a larger network.

Example:

```text
             Router
                |
        ┌───────┼───────┐
        |       |       |
       LAN    Servers  Guests
```

Each segment can have different addressing, access, and security requirements.

---

3. LAN Segmentation

A LAN can be divided into multiple network segments.

Example:

```text
                Router
                  |
             Main Network
                  |
        ┌─────────┼─────────┐
        |         |         |
     Users     Servers    Guests
```

This can make it easier to control communication between different groups.

---

4. Broadcast Domains

A broadcast domain is the group of devices that receive a Layer 2 broadcast.

Routers can separate broadcast domains.

```text
Broadcast Domain A
        |
        |
      Router
        |
        |
Broadcast Domain B
```

Broadcast traffic from one side does not normally cross a router into the other broadcast domain.

---

5. Collision Domains

A collision domain is a network area in which simultaneous transmissions can potentially interfere with each other.

A hub creates a shared collision domain.

```text
PC1 ──┐
PC2 ──┼── Hub
PC3 ──┘
```

With a switch, each switch port is typically a separate collision domain.

```text
PC1 ──┐
      |
    Switch
      |
PC2 ──┘
```

---

6. Router-Based Segmentation

A router can connect different IP networks.

Example:

```text
192.168.10.0/24
        |
        |
      Router
        |
        |
192.168.20.0/24
```

The router separates the two networks and can make routing decisions between them.

---

7. DMZ

DMZ stands for Demilitarized Zone.

A DMZ is a network segment designed to isolate publicly accessible services from an internal network.

A simplified design:

```text
                 Internet
                    |
                 Firewall
                    |
             ┌──────┴──────┐
             |             |
            DMZ         Internal LAN
             |
        Public Services
```

Servers that need to be reachable from outside the organization can be placed in a DMZ.

Examples may include:

· Web servers
· Public-facing services

The exact architecture depends on the network design and security requirements.

---

8. Firewall and Segmentation

A firewall can control traffic between network segments.

Example:

```text
Internet
   |
Firewall
   |
   +------ DMZ
   |
   +------ Internal Network
```

The firewall can apply rules to determine which traffic is allowed or blocked.

Segmentation and firewall rules can work together to limit unnecessary communication between network areas.

---

9. Security Benefits

Segmentation can reduce the impact of a security incident.

For example:

```text
Compromised Device
        |
     Segment A
        |
    Restricted
        |
     Segment B
```

If communication between segments is restricted, a compromised device may have fewer opportunities to communicate with other systems.

Segmentation is therefore an important part of network security design.

---

10. Performance Benefits

Segmentation can also help manage network traffic.

Separating devices into different segments can reduce unnecessary broadcast traffic within each segment.

Example:

```text
Segment A          Segment B

PC1                 PC4
PC2                 PC5
PC3                 PC6
```

Traffic intended for one segment does not automatically need to reach every device in another segment.

---

11. Network Segmentation Example

Consider an organization with:

· Users
· Servers
· Guest Devices
· Security Cameras

A possible design could be:

```text
                    Firewall
                       |
                    Router
                       |
        ┌──────────────┼──────────────┐
        |              |              |
      Users          Servers        Guests
```

Security cameras could also be placed in a separate network segment:

```text
                    Router
                       |
        ┌──────────────┼──────────────┐
        |              |              |
      Users          Servers        Cameras
                                      |
                                    Guests
```

The actual design depends on the organization's requirements.

---

12. Segmentation and Access Control

Segmentation does not automatically make a network secure.

Traffic between segments still needs appropriate access control.

For example:

```text
Users ───────> Servers
   Allowed

Guests ──────X──────> Internal Servers
   Blocked
```

A firewall or router can enforce rules between different networks.

---

13. Internet, DMZ, and Internal Network

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

Segmentation Comparison

Concept Main Purpose
Network Segment Separates part of a network
Broadcast Domain Defines where Layer 2 broadcasts are received
Collision Domain Defines an area where collisions can occur
Router Connects different IP networks
Firewall Controls traffic between networks
DMZ Isolates public-facing services

---

Key Takeaways

· Network segmentation divides a network into separate areas.
· Segmentation can improve organization, security, and traffic management.
· Routers can separate different IP networks.
· Routers separate broadcast domains.
· Switch ports normally represent separate collision domains.
· A DMZ can isolate public-facing services from an internal network.
· Firewalls can control communication between network segments.
· Segmentation alone does not provide complete security.
· Appropriate access-control rules are required between segments.

---

Practice

1. What is network segmentation?
2. Why might an organization divide its network into multiple segments?
3. What is a broadcast domain?
4. What is a collision domain?
5. How can a router separate network segments?
6. What is a DMZ?
7. Why might public-facing servers be placed in a DMZ?
8. How can a firewall control communication between segments?
9. Explain one security benefit of network segmentation.
10. Explain the difference between a broadcast domain and a collision domain.
