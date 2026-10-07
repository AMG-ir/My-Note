Network Types

Computer networks can be classified based on their geographic coverage, purpose, communication environment, and how devices are connected.

1. LAN

LAN stands for Local Area Network.

A LAN connects devices within a relatively small geographic area.

Examples include:

· Home networks
· School networks
· Office networks
· Computer labs

A simple LAN:

```text
        Switch
       /  |  \
      /   |   \
    PC   PC   Printer
```

Common characteristics:

· Limited geographic area
· High-speed local communication
· Usually managed by a single organization or individual

---

2. MAN

MAN stands for Metropolitan Area Network.

A MAN connects multiple networks across a larger geographic area, typically covering a city or metropolitan area.

A simplified example:

```text
Network A
          |
          |
      City Network
       /       \
      /         \
Network B     Network C
```

A MAN is larger than a LAN but generally smaller in scope than a WAN.

---

3. WAN

WAN stands for Wide Area Network.

A WAN connects networks across large geographic distances.

It can connect:

· Cities
· Countries
· Regions
· Different organizational locations

A simplified WAN:

```text
LAN A
  |
Router
  |
  +-------- WAN --------+
                       |
                     Router
                       |
                      LAN B
```

WANs are used when networks need to communicate across long distances.

---

4. Internet

The Internet is a global system of interconnected networks.

It connects networks around the world and allows devices and services to communicate using standardized networking protocols.

A simplified structure:

```text
Local Network
      |
    Router
      |
   Internet
      |
    Router
      |
Remote Network
```

The Internet is not a single physical network. It is a network of interconnected networks.

---

5. Intranet

An intranet is a private network used within an organization.

It can provide internal services and resources to authorized users.

Examples include:

· Internal websites
· Internal applications
· Internal file resources
· Organizational services

```text
Employees
    |
    v
Private Network
    |
    +---- Internal Services
    |
    +---- Internal Resources
```

An intranet is intended primarily for internal use.

---

6. Extranet

An extranet is a private network or private network environment that provides controlled access to selected resources for authorized external users.

External users may include:

· Business partners
· Suppliers
· Customers
· Other authorized organizations

A simplified example:

```text
Internal Users
      |
      v
Private Network
      |
      +---- Internal Resources
      |
      +---- Controlled External Access
                    |
                    v
             External Users
```

The important concept is controlled access rather than unrestricted public access.

---

7. LAN vs MAN vs WAN

Type Geographic Scope Example
LAN Small area Home or office
MAN City or metropolitan area Multiple networks across a city
WAN Large geographic area Networks across countries
Internet Global Global interconnected networks

---

8. Wired Networks

A wired network uses physical transmission media to connect devices.

Examples include:

· Ethernet cables
· Copper-based connections
· Fiber-optic connections

A basic wired network:

```text
Computer
    |
 Ethernet
    |
  Switch
    |
 Ethernet
    |
 Server
```

Wired networks are commonly used in offices, data centers, homes, and other network environments.

---

9. Wireless Networks

A wireless network uses radio communication instead of a physical cable for the network connection.

A common example is Wi-Fi.

```text
Wireless
      /    |    \
     /     |     \
   PC    Phone   Laptop
        Access Point
```

Wireless networking is covered in more detail in:

Wireless Networking

---

10. Point-to-Point Network

A point-to-point connection directly connects two endpoints.

```text
Device A ───────── Device B
```

The connection is between two endpoints rather than being shared among multiple endpoints.

Point-to-point communication can be used in different network technologies and environments.

---

11. Client-Server Network

In a client-server network, clients request services or resources from servers.

```text
Client 1 ──┐
Client 2 ──┼──> Server
Client 3 ──┘
```

Examples of services that can be provided by servers include:

· File services
· Web services
· Network services
· Application services

---

12. Peer-to-Peer Network

In a peer-to-peer network, devices can communicate directly with each other and can provide resources or services to other devices.

```text
Device A ───── Device B
    \             /
     \           /
      Device C
```

There is not necessarily a dedicated central server for every service.

---

13. Network Classification by Scope

A simplified classification based on geographic scope is:

```text
LAN
 ↓
MAN
 ↓
WAN
 ↓
Internet
```

As the geographic scope increases, the network can connect a larger number of locations and networks.

---

14. Network Classification by Access

Networks can also be classified by who is allowed to access their resources.

Public

Resources are available to the public.

Example:

· Internet

Private

Resources are restricted to authorized users.

Examples:

· Company LAN
· School Network
· Intranet

Controlled External Access

Selected external users can access specific resources.

Example:

· Extranet

---

15. Specialized Wireless Network Types

Some wireless networks are designed for specific environments and types of moving devices.

MANET

MANET stands for Mobile Ad Hoc Network.

It is a wireless network in which mobile devices can communicate without relying on a fixed infrastructure in the traditional way.

VANET

VANET stands for Vehicular Ad Hoc Network.

It is designed for communication involving vehicles and other participating network devices.

FANET

FANET stands for Flying Ad Hoc Network.

It is designed for communication between flying devices such as unmanned aerial vehicles.

These specialized wireless networks are covered in more detail in:

Wireless Networking

---

16. Network Types Comparison

Network Type Main Characteristic
LAN Small local area
MAN Metropolitan or city-wide area
WAN Large geographic area
Internet Global interconnected networks
Intranet Private internal network
Extranet Controlled external access to private resources
Point-to-Point Direct connection between two endpoints
MANET Mobile ad hoc wireless network
VANET Vehicular ad hoc wireless network
FANET Flying ad hoc wireless network

---

Key Takeaways

· LANs cover relatively small areas.
· MANs can connect networks across a metropolitan area.
· WANs connect networks over large geographic distances.
· The Internet is a global network of interconnected networks.
· An intranet is a private internal network.
· An extranet provides controlled access to selected private resources for authorized external users.
· Wired networks use physical transmission media.
· Wireless networks use wireless communication.
· Point-to-point communication connects two endpoints.
· Client-server networks use servers to provide services to clients.
· Peer-to-peer networks allow devices to communicate and share resources directly.
· MANET, VANET, and FANET are specialized types of wireless ad hoc networks.

---

Practice

Practice 1

Classify each example:

· Home network
· University network across several buildings
· Network connecting offices in different cities
· Global interconnected networks

Use:

· LAN
· MAN
· WAN
· Internet

Practice 2

Explain the difference between:

· LAN
· MAN
· WAN

Practice 3

Explain the difference between:

· Internet
· Intranet
· Extranet

Practice 4

Identify the network type:

```text
Device A ───────── Device B
```

Practice 5

Explain the difference between a client-server network and a peer-to-peer network.

Practice 6

Explain the purpose of:

· MANET
· VANET
· FANET
