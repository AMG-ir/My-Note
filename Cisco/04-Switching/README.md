# 04 - Switching

This section documents the switching concepts studied as part of Cisco networking.

## What Is a Switch

A network switch connects devices within a local area network (LAN) and forwards Ethernet frames based on destination MAC addresses.

## MAC Address Table

A switch learns source MAC addresses from incoming Ethernet frames and associates them with the ports on which they were received. The switch uses its MAC address table to forward known unicast traffic toward the appropriate port.

## How a Switch Forwards Frames

A switch generally handles Ethernet frames in the following ways:

| Frame Type       | Behavior |
|------------------|----------|
| Known unicast    | Forwards the frame toward the port associated with the destination MAC address |
| Unknown unicast  | Floods the frame within the relevant VLAN, except through the incoming port |
| Broadcast        | Floods the frame within the relevant VLAN, except through the incoming port |

## Switching and VLANs

- A VLAN defines a separate Layer 2 broadcast domain.
- A switch can support multiple VLANs.
- Access ports normally carry traffic for one VLAN.
- Trunk ports can carry traffic for multiple VLANs.

## Useful Commands

| Command                   | Purpose |
|---------------------------|---------|
| `show mac address-table`  | Display the switch MAC address table |
| `show vlan brief`         | Display VLAN information |
| `show interfaces`         | Display interface information |

## Key Takeaways

- Switches forward Ethernet frames using MAC address information.
- MAC address tables associate learned MAC addresses with switch ports and VLANs.
- VLANs separate Layer 2 broadcast domains.
- Switching behavior depends on the destination MAC address and VLAN.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
