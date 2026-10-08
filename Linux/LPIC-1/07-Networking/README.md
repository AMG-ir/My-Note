# 07 - Networking

This section covers basic Linux networking commands and concepts, including network interfaces, IP addresses, routing, neighbor information, connectivity testing, and network configuration.

## Overview

Linux provides several commands for inspecting and managing network interfaces and network connectivity.

The main topics covered in this section are:

- Network interfaces
- IP addresses
- MAC addresses
- Network routes
- ARP and neighbor information
- Connectivity testing
- Promiscuous mode
- Legacy networking tools

## Contents

- [Network Interfaces](#network-interfaces)
- [ip](#ip)
- [ip address](#ip-address)
- [ip link](#ip-link)
- [ip route](#ip-route)
- [ip neighbor](#ip-neighbor)
- [ping](#ping)
- [traceroute](#traceroute)
- [Legacy Tools](#legacy-tools)
- [Promiscuous Mode](#promiscuous-mode)
- [Network Troubleshooting](#network-troubleshooting)
- [Useful Commands](#useful-commands)
- [Practical Examples](#practical-examples)
- [Key Takeaways](#key-takeaways)

---

## Network Interfaces

A network interface connects a Linux system to a network. Interfaces can be physical or virtual.

Common interface information includes:

- Interface name
- MAC address
- IP address
- Interface state

---

## ip

The `ip` command is used to view and manage network configuration.

Basic syntax:

```bash
ip [object] [command]
```

Common objects include:

```text
address
link
route
neighbor
```

---

## ip address

Displays IP address information for network interfaces.

```bash
ip address
```

Short form:

```bash
ip addr
```

Example output can contain information such as:

```text
inet 192.168.1.10/24
```

This represents an IPv4 address and its prefix length.

### Viewing a Specific Interface

```bash
ip address show dev eth0
```

> **Note:** The interface name depends on the system.

---

## ip link

Displays information about network interfaces.

```bash
ip link
```

It can show information such as:

- Interface name
- Interface state
- MAC address
- Link information

### Checking Interface State

An interface can have states such as:

```text
UP
DOWN
```

For example:

```text
state UP
```

indicates that the interface is administratively up.

### MAC Address

A MAC address is a hardware-level address associated with a network interface. It can be viewed using `ip link`.

```text
link/ether 00:11:22:33:44:55
```

---

## ip route

Displays the system routing table.

```bash
ip route
```

A typical routing table can contain entries such as:

```text
default via 192.168.1.1 dev eth0
192.168.1.0/24 dev eth0
```

### Default Route

The default route is used when no more specific route exists for the destination.

```text
default via 192.168.1.1 dev eth0
```

This means traffic that does not match another route can be sent through the specified gateway.

---

## ip neighbor

Displays information about neighboring devices. It can show information associated with devices reachable on the local network.

```bash
ip neighbor
```

Example output:

```text
192.168.1.1 dev eth0 lladdr 00:11:22:33:44:55 REACHABLE
```

Neighbor information is associated with IP and MAC addresses.

---

## ping

Tests network connectivity between the local system and a destination.

```bash
ping 8.8.8.8
```

A hostname can also be used:

```bash
ping example.com
```

The command sends ICMP Echo Requests and waits for replies.

### Basic ping Options

To send a specific number of packets:

```bash
ping -c 4 8.8.8.8
```

This sends four ICMP Echo Requests.

### Understanding ping Results

A successful response can look similar to:

```text
64 bytes from 8.8.8.8: icmp_seq=1 ttl=117 time=20 ms
```

Important information includes:

- Destination
- Sequence number
- TTL
- Response time

If there is no response, possible reasons include:

- Destination is unreachable
- Network configuration problem
- Firewall filtering
- The destination does not respond to ICMP

---

## traceroute

Displays the path packets take toward a destination.

```bash
traceroute example.com
```

It can help identify where traffic travels between the local system and a destination.

---

## Legacy Tools

### ifconfig

`ifconfig` is a legacy networking command used to display and configure network interfaces.

```bash
ifconfig
```

It can display information such as:

- Interface names
- IP addresses
- MAC addresses
- Interface status
- Packet statistics

> **Note:** Modern Linux systems generally use the `ip` command for network configuration.

### route

`route` is a legacy command for viewing and managing the IP routing table.

```bash
route
```

The routing table can also be viewed using:

```bash
ip route
```

### net-tools

`net-tools` is a package that provides several traditional networking utilities. It includes commands such as:

```text
ifconfig
route
```

On systems where these commands are not installed, the `net-tools` package may be required.

---

## Promiscuous Mode

In normal operation, a network interface generally processes traffic intended for it. In promiscuous mode, the interface can receive network frames that are not necessarily addressed to its own MAC address.

This mode can be relevant when analyzing network traffic.

The interface state can be inspected with:

```bash
ip link
```

An interface operating in promiscuous mode may show:

```text
PROMISC
```

---

## Network Troubleshooting

A basic network troubleshooting process can start with checking the local interface configuration.

1. Check interfaces:

   ```bash
   ip link
   ```

2. Check IP addresses:

   ```bash
   ip address
   ```

3. Check the routing table:

   ```bash
   ip route
   ```

4. Check neighbor information:

   ```bash
   ip neighbor
   ```

5. Test connectivity:

   ```bash
   ping 8.8.8.8
   ```

6. Test name resolution:

   ```bash
   ping example.com
   ```

7. Trace the network path:

   ```bash
   traceroute example.com
   ```

---

## Useful Commands

| Command       | Purpose |
|---------------|---------|
| `ip address`  | Display IP address information |
| `ip link`     | Display network interface information |
| `ip route`    | Display the routing table |
| `ip neighbor` | Display neighbor information |
| `ping`        | Test network connectivity |
| `traceroute`  | Display the path to a destination |
| `ifconfig`    | Display legacy interface information |
| `route`       | Display the legacy routing table |
| `net-tools`   | Package containing traditional networking utilities |

---

## Practical Examples

### View Network Interfaces

```bash
ip link
```

### View IP Addresses

```bash
ip address
```

### View a Specific Interface

```bash
ip address show dev eth0
```

### View the Routing Table

```bash
ip route
```

### View Neighbor Information

```bash
ip neighbor
```

### Test Connectivity to an IP Address

```bash
ping 8.8.8.8
```

### Test Connectivity Four Times

```bash
ping -c 4 8.8.8.8
```

### Test Connectivity Using a Hostname

```bash
ping example.com
```

### Trace a Route

```bash
traceroute example.com
```

### View Legacy Interface Information

```bash
ifconfig
```

### View the Legacy Routing Table

```bash
route
```

---

## Key Takeaways

- Network interfaces provide network connectivity to the Linux system.
- `ip address` displays IP address information.
- `ip link` displays network interface information.
- MAC addresses can be viewed with `ip link`.
- `ip route` displays the routing table.
- `ip neighbor` displays information about neighboring devices.
- `ping` can be used to test network connectivity.
- `traceroute` can be used to inspect the path toward a destination.
- `ifconfig` and `route` are traditional networking commands.
- Promiscuous mode allows a network interface to receive traffic beyond normal destination filtering.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
