Cisco CLI and Commands

This section documents the Cisco IOS command-line interface (CLI) and the commands used to inspect device status and configure networking equipment.

1. Entering CLI Modes

Command| Purpose
"enable"| Enter Privileged EXEC mode
"configure terminal"| Enter Global Configuration mode
"interface <type> <number>"| Enter interface configuration mode
"exit"| Return to the previous configuration level
"end"| Return to Privileged EXEC mode

2. Viewing Device Information

Command| Purpose
"show running-config"| Display the active configuration
"show startup-config"| Display the saved startup configuration
"show interfaces"| Display interface information
"show ip interface brief"| Show a summary of IP addresses and interface status
"show version"| Display device and IOS information

3. Saving Configuration

Command| Purpose
"copy running-config startup-config"| Save the active configuration
"show startup-config"| Verify the saved configuration

4. Basic Configuration Example

enable
configure terminal
hostname Switch1
interface fastEthernet 0/1
exit
end
copy running-config startup-config

This example changes the hostname, enters an interface configuration mode, and saves the configuration. No interface settings are changed in this example.

5. Important Notes

- Commands must be entered in the appropriate CLI mode.
- The available interfaces and interface names depend on the device model.
- "running-config" contains the current configuration.
- "startup-config" contains the saved configuration used during startup.

Status

In progress.
