# 11 - Wireless Networking

Wireless networking allows devices to communicate without a physical network cable by using radio signals. Wireless networks are commonly used for local connectivity, mobile communication, and specialized network environments.

## Contents

- [Wi-Fi](#wi-fi)
- [IEEE 802.11](#ieee-80211)
- [2.4 GHz and 5 GHz](#24-ghz-and-5-ghz)
- [Wireless Network Components](#wireless-network-components)
- [Wireless LAN](#wireless-lan)
- [Wireless Network Modes](#wireless-network-modes)
- [MANET, VANET, and FANET](#manet-vanet-and-fanet)
- [Wireless Interference](#wireless-interference)
- [Wireless Range](#wireless-range)
- [Wireless Security](#wireless-security)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## Wi-Fi

Wi-Fi is commonly associated with the IEEE 802.11 family of wireless LAN standards. A basic wireless network can look like:

```text
Laptop
   |
 Wi-Fi
   |
Access Point
   |
Switch
   |
Network
```

The Access Point provides wireless connectivity to client devices.

---

## IEEE 802.11

IEEE 802.11 is a family of standards for Wireless Local Area Networks. Different 802.11 standards and amendments provide different capabilities, frequencies, speeds, and features.

Wi-Fi commonly operates in the following frequency bands:

- 2.4 GHz
- 5 GHz

---

## 2.4 GHz and 5 GHz

### 2.4 GHz

The 2.4 GHz band is widely used for wireless communication.

- Longer typical range than 5 GHz
- Better propagation through many obstacles
- More susceptible to interference
- Fewer non-overlapping channels

A 2.4 GHz network can be useful when coverage and range are more important than maximum performance.

### 5 GHz

The 5 GHz band is also widely used for Wi-Fi.

- More available channels
- Often provides higher performance
- Generally shorter range than 2.4 GHz
- More affected by walls and other obstacles

### Comparison

| Feature             | 2.4 GHz         | 5 GHz |
|---------------------|-----------------|-------|
| Typical Range       | Longer          | Shorter |
| Wall Penetration    | Better          | Lower |
| Interference        | Usually higher  | Usually lower |
| Available Channels  | Fewer           | More |
| Typical Performance | Lower           | Higher |
| Coverage            | Wider           | More limited |

> **Note:** Neither frequency is always better. The appropriate choice depends on the environment and requirements. Actual performance depends on the wireless standard, hardware, channel configuration, distance, and environment.

---

## Wireless Network Components

### Wireless Client

A wireless client is a device that connects to a wireless network, such as a laptop, smartphone, or tablet.

### Access Point

An Access Point provides wireless network access to client devices.

```text
Wireless Clients
   |   |   |
     Wi-Fi
       |
 Access Point
       |
    Network
```

### Wireless Network Interface

A wireless network interface allows a device to communicate using Wi-Fi. It has a MAC address used for network communication.

---

## Wireless LAN

A Wireless LAN (WLAN) provides network connectivity through wireless communication within a local area.

```text
          Laptop
             |
           Wi-Fi
             |
Phone --- Access Point --- Network
             |
           Wi-Fi
             |
          Tablet
```

A WLAN can provide network access without requiring an Ethernet cable for each client.

---

## Wireless Network Modes

### Infrastructure Mode

In infrastructure mode, wireless clients communicate through an Access Point.

```text
Laptop --+
         |
Phone --- Access Point --- Network
         |
Tablet --+
```

### Ad Hoc Mode

In an ad hoc network, wireless devices communicate directly with each other without requiring a traditional Access Point.

```text
Laptop <--------> Laptop
   ^                ^
    \              /
     \            /
      Smartphone
```

---

## MANET, VANET, and FANET

### MANET

MANET stands for Mobile Ad Hoc Network. It is a network formed by mobile devices that can communicate without relying on fixed network infrastructure.

```text
Node A <----> Node B
  ^             |
  |             |
  v             v
Node C <----> Node D
```

- Mobile nodes
- Dynamic network topology
- No fixed infrastructure required
- Nodes can communicate with each other

### VANET

VANET stands for Vehicular Ad Hoc Network. It is a specialized type of mobile ad hoc network involving vehicles.

```text
Car A <----> Car B <----> Car C
```

Vehicles can communicate with other vehicles or network infrastructure.

- Vehicles act as network nodes.
- Nodes are highly mobile.
- Network topology can change quickly.
- Communication can support vehicle-related applications.

### FANET

FANET stands for Flying Ad Hoc Network. It is an ad hoc network involving flying devices such as unmanned aerial vehicles.

```text
Drone A <----> Drone B
    \            /
     \          /
      Drone C
```

- Flying mobile nodes
- Highly dynamic topology
- Rapid changes in node position
- Wireless communication between nodes

### Comparison

| Feature           | MANET                      | VANET                      | FANET |
|-------------------|----------------------------|----------------------------|-------|
| Full Name         | Mobile Ad Hoc Network      | Vehicular Ad Hoc Network   | Flying Ad Hoc Network |
| Main Nodes        | Mobile devices             | Vehicles                   | Flying devices |
| Mobility          | High                       | Very High                  | Very High |
| Topology Changes  | Dynamic                    | Very Dynamic               | Very Dynamic |
| Infrastructure    | Not necessarily required   | Not necessarily required   | Not necessarily required |

---

## Wireless Interference

Wireless communication can be affected by interference. Possible sources include:

- Other wireless networks
- Other devices using the same frequency
- Physical obstacles
- Distance
- Environmental conditions

Interference can reduce wireless performance and reliability.

---

## Wireless Range

Wireless range depends on several factors:

- Frequency
- Transmit power
- Antenna
- Obstacles
- Distance
- Environment
- Wireless standard

> **Note:** Higher frequency does not automatically mean better coverage.

---

## Wireless Security

Wireless networks need appropriate security controls to protect network communication. Important considerations include:

- Authentication
- Encryption
- Secure wireless configuration
- Strong access credentials

Wireless security is especially important because radio signals can extend beyond the physical boundaries of a building.

---

## Key Takeaways

- Wi-Fi is commonly associated with IEEE 802.11.
- Wireless networks use radio communication instead of physical cables.
- 2.4 GHz generally provides greater range but is more susceptible to interference.
- 5 GHz generally provides higher performance but has shorter typical range.
- An Access Point provides wireless network access to clients.
- A WLAN provides local network connectivity through wireless communication.
- Infrastructure mode uses an Access Point.
- Ad hoc networks allow devices to communicate without traditional fixed infrastructure.
- MANET consists of mobile nodes.
- VANET focuses on communication involving vehicles.
- FANET focuses on communication involving flying devices.
- Wireless performance depends on frequency, distance, obstacles, interference, hardware, and environment.

---

## Practice

- What is Wi-Fi commonly associated with?
- What is the difference between 2.4 GHz and 5 GHz?
- What is the role of an Access Point?
- What is a WLAN?
- Explain infrastructure mode.
- What is an ad hoc network?
- What does MANET stand for?
- What is the difference between MANET and VANET?
- What does FANET stand for?
- Name three factors that can affect wireless range.
- Why can wireless networks be affected by interference?
- Compare MANET, VANET, and FANET.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
