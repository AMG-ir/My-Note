VLANs and Trunking

This section documents VLAN concepts and switch port configuration using Cisco IOS.

1. What Is a VLAN?

A Virtual LAN (VLAN) logically separates a switched network into different Layer 2 broadcast domains.

Devices in different VLANs generally require a Layer 3 device to communicate with each other.

2. Access and Trunk Ports

Port Type| Purpose
Access| Carries traffic for a single VLAN under normal configurations
Trunk| Carries traffic for multiple VLANs between compatible network devices

3. VLAN Configuration

Create a VLAN

enable
configure terminal
vlan 10
name Sales
exit

This creates VLAN 10 and assigns it the name "Sales".

Assign a Switch Port to a VLAN

interface fastEthernet 0/1
switchport mode access
switchport access vlan 10
exit

This configures the selected switch port as an access port assigned to VLAN 10.

4. Trunk Port Configuration

interface gigabitEthernet 0/1
switchport mode trunk
exit

This configures the selected interface as a trunk port on devices that support this command and configuration.

5. Verification Commands

Command| Purpose
"show vlan brief"| Display VLANs and their assigned ports
"show interfaces trunk"| Display trunk port information

6. Important Notes

- VLANs separate Layer 2 broadcast domains.
- Access ports normally belong to one VLAN.
- Trunk ports can carry traffic for multiple VLANs.
- Communication between different VLANs requires Layer 3 routing.
- Available commands and interface names may vary by device model.

Status

In progress.
