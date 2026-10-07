Networking Fundamentals

This section covers the fundamental concepts required to understand computer networks and how networked devices communicate.

1. What Is a Network?

A computer network is a group of connected devices that can communicate and exchange data with each other.

Networked devices can include:

· Computers
· Servers
· Routers
· Switches
· Network printers
· Wireless devices
· Other network-connected systems

The purpose of networking is to allow devices to communicate and share resources and information.

---

2. Network Communication

Network communication is the process of exchanging data between devices.

A basic communication path can be represented as:

```text
Source → Network → Destination
```

For example:

```text
Computer A → Switch → Router → Network → Server
```

The exact path depends on the network architecture and the devices involved.

---

3. Hosts and Nodes

A host is a device connected to a network that can send or receive data.

Examples include:

· Computers
· Servers
· Smartphones
· Network printers

A node is a device or connection point that participates in a network.

The terms host and node can overlap, but they are not always interchangeable in every networking context.

---

4. Client and Server

Client

A client is a device or application that requests a service or resource.

Examples:

· A web browser requesting a web page
· A computer requesting a file from a server

Server

A server provides services or resources to clients.

Examples:

· Web server
· File server
· DNS server
· Mail server

A basic client-server model looks like:

```text
Client → Request → Server
Client ← Response ← Server
```

---

5. Point-to-Point Communication

Point-to-point communication is a direct communication relationship between two endpoints.

```text
Device A ───────── Device B
```

The communication path is between the two endpoints rather than being shared among multiple endpoints.

Point-to-point connections can be used in different networking technologies and environments.

---

6. Internet

The Internet is a global network of interconnected networks.

It connects networks and devices around the world and allows them to communicate using standardized networking protocols.

A simplified representation:

```text
Local Network
      |
      v
    Router
      |
      v
  Internet
      |
      v
Remote Network
```

---

7. Intranet

An intranet is a private network used within an organization.

It can provide internal services and resources to authorized users.

Examples include:

· Internal websites
· Internal applications
· Shared resources
· Internal communication systems

A simplified structure:

```text
Users
  |
  v
Internal Network
  |
  +---- Internal Services
  |
  +---- Internal Resources
```

An intranet is generally not intended to provide unrestricted public access.

---

8. Extranet

An extranet extends selected resources or services of a private network to authorized external users or organizations.

For example, a company may provide selected services to:

· Business partners
· Suppliers
· Customers
· External organizations

The important concept is controlled access to selected private resources.

---

9. Network Architecture

Network architecture describes how network devices, systems, services, and communication paths are organized.

A network can contain different components such as:

```text
Clients
   |
Switches
   |
Routers
   |
Servers
   |
Network Services
```

The architecture depends on the requirements of the network.

---

10. Network Resources

Networking allows devices to access and share resources.

Examples include:

· Files
· Applications
· Internet access
· Printers
· Servers
· Network services

Resource sharing is one of the fundamental purposes of computer networking.

---

11. Network Communication Models

Different network environments can use different communication models.

Client-Server

A client requests services from a server.

```text
Client 1 ──┐
Client 2 ──┼──> Server
Client 3 ──┘
```

Peer-to-Peer

Devices can communicate directly with each other without requiring a dedicated central server for every service.

```text
Device A ─── Device B
    \          /
     \        /
      Device C
```

---

12. Network Devices

Networks use different devices for different purposes.

Common examples include:

Device Basic Role
NIC Provides network connectivity to a device
Switch Connects devices within a network
Router Connects different networks
Bridge Connects network segments
Gateway Provides a connection between different networks or systems
Firewall Controls network traffic based on security rules
Access Point Provides wireless network connectivity

The detailed operation of these devices is covered in the Network Devices section.

---

13. Local and Remote Communication

Communication can occur between devices on the same local network or between devices on different networks.

Local Communication

```text
Computer A
    |
  Switch
    |
Computer B
```

Communication Between Networks

```text
Computer A
    |
  Switch
    |
  Router
    |
  Network
    |
  Router
    |
  Switch
    |
Computer B
```

Routers are used when communication needs to pass between different networks.

---

14. Basic Network Structure

A simple network can contain:

```text
              Internet
              |
           Router
              |
           Switch
         /    |    \
        /     |     \
   Client   Server   Client
```

Each component has a different role in communication.

---

15. Network Communication Fundamentals

Several basic concepts are important when studying networking:

· Devices need a way to communicate.
· Communication requires agreed-upon rules and protocols.
· Different devices can have different roles.
· Networks can be connected to other networks.
· Network devices control or forward traffic according to their function.
· Network communication can occur locally or across multiple networks.

---

Key Takeaways

· A network connects devices so they can communicate and share resources.
· Hosts and nodes participate in network communication.
· Clients request services or resources.
· Servers provide services or resources.
· Point-to-point communication connects two endpoints.
· The Internet is a global network of interconnected networks.
· An intranet is a private internal network.
· An extranet provides controlled access to selected private resources for external users.
· Network architecture describes how network components are organized.
· Switches, routers, bridges, gateways, and firewalls have different roles in a network.

---

Practice

Practice 1

Identify the client and server in the following communication:

```text
Computer → Web Service
```

Practice 2

Identify whether the following represents point-to-point communication:

```text
Device A ───────── Device B
```

Practice 3

Identify whether the following is a local or inter-network communication path:

```text
Computer A → Switch → Computer B
```

Practice 4

Identify the role of each device:

```text
Client → Switch → Router → Internet
```

Practice 5

Explain the difference between:

· Internet
· Intranet
· Extranet
