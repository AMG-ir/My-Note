# 05 - Routing

This section documents the routing concepts studied as part of Cisco networking.

## Contents

- [What Is Routing](#what-is-routing)
- [What Is a Router](#what-is-a-router)
- [Routing Table](#routing-table)
- [Static and Dynamic Routing](#static-and-dynamic-routing)
- [Basic Router Interface Configuration](#basic-router-interface-configuration)
- [Key Takeaways](#key-takeaways)

---

## What Is Routing

Routing is the process of selecting a path for IP packets to travel from one network to another. Routers use routing tables to determine where packets should be forwarded.

---

## What Is a Router

A router connects different IP networks and forwards packets between them. Each router interface connected to a network normally requires an appropriate IP address and subnet mask.

---

## Routing Table

A routing table contains information that helps a router determine how to forward packets toward their destinations. A router may use:

- Directly connected routes
- Static routes
- Routes learned through dynamic routing protocols

---

## Static and Dynamic Routing

| Type            | Description |
|-----------------|-------------|
| Static Routing  | Routes are manually configured by an administrator. |
| Dynamic Routing | Routers learn and update routes using routing protocols. |

---

## Basic Router Interface Configuration

```text
enable
configure terminal
interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
end
```

This example assigns an IPv4 address to a router interface and enables it.

> **Note:** The interface name and addressing must match the actual network topology.

---

## Key Takeaways

- Routing allows communication between different IP networks.
- A router uses its routing table to select a forwarding path.
- Static routes are configured manually.
- Dynamic routing protocols allow routers to exchange routing information.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
