# Snort 3 Network Scan Detection

- **Category:** Networking, Network Security
- **Status:** In Progress

## Overview

This lab explores network scan detection and traffic prevention using Snort 3 on Linux. The experiment involves generating network traffic with Nmap, creating custom Snort rules, analyzing TCP traffic, and investigating how suspicious scanning activity can be detected and blocked.

The main objective is to understand how Snort 3 processes network traffic, generates alerts, and applies rule-based actions in an appropriate IPS configuration.

## Contents

- [Objectives](#objectives)
- [Environment](#environment)
- [Snort 3 Command-Line Basics](#snort-3-command-line-basics)
- [Snort Rule Structure](#snort-rule-structure)
- [Rule Actions](#rule-actions)
- [Network Scan Detection with Nmap](#network-scan-detection-with-nmap)
- [TCP Traffic Analysis](#tcp-traffic-analysis)
- [IDS and IPS](#ids-and-ips)
- [Detection and Prevention Considerations](#detection-and-prevention-considerations)
- [Troubleshooting Checklist](#troubleshooting-checklist)
- [Further Investigation](#further-investigation)

---

## Objectives

- Run Snort 3 on Linux.
- Understand essential Snort command-line options.
- Create and load custom detection rules.
- Investigate network scanning using Nmap.
- Detect suspicious traffic and generate alerts.
- Understand the difference between IDS and IPS operation.
- Investigate blocking network traffic through Snort rules.
- Understand how network visibility and rule configuration affect detection.

---

## Environment

| Component           | Description |
|---------------------|-------------|
| Operating system    | Linux |
| Detection engine    | Snort 3 |
| Scanning tool       | Nmap |
| Packet analysis tool| Wireshark |
| Detection method    | Custom Snort rules |
| Primary objective   | Network scan detection and traffic prevention |

---

## Snort 3 Command-Line Basics

### Check the Installed Version

```bash
snort -V
```

Displays information about the installed Snort version.

### Display Command-Line Help

```bash
snort --help
```

Displays available command-line options.

### Validate the Configuration

```bash
sudo snort -T -c /etc/snort/snort.lua
```

Checks the Snort configuration for errors. The configuration path may differ depending on the installation.

### Run Snort on a Network Interface

```bash
sudo snort -c /etc/snort/snort.lua -i eth0
```

Starts Snort using the specified configuration and network interface. Replace `eth0` with the actual interface name.

### Load Custom Rules and Display Alerts

```bash
sudo snort -c /etc/snort/snort.lua \
  -R /etc/snort/rules/local.rules \
  -i eth0 -A alert_fast
```

Loads a custom rule file and uses the fast alert output format.

| Option           | Description |
|------------------|-------------|
| `-V`             | Displays version information |
| `--help`         | Displays command-line help |
| `-T`             | Tests the configuration |
| `-c`             | Specifies the configuration file |
| `-R`             | Loads an additional rule file |
| `-i`             | Selects the network interface |
| `-A alert_fast`  | Selects fast alert output |

> **Note:** These examples use common Snort 3 command-line options. File paths and interface names must match the actual environment.

---

## Snort Rule Structure

Snort rules define which network traffic should match a condition and what action should occur when a match is found. A simplified rule structure:

```text
action protocol source_ip source_port -> destination_ip destination_port (options)
```

### Rule Components

| Component         | Description |
|-------------------|-------------|
| `action`          | Defines the action taken on a match |
| `protocol`        | Specifies the network protocol |
| `source_ip`       | Defines the source address |
| `source_port`     | Defines the source port |
| `->`              | Specifies traffic direction |
| `destination_ip`  | Defines the destination address |
| `destination_port`| Defines the destination port |
| `options`         | Contains matching conditions and rule metadata |

### Example: Basic TCP Alert Rule

```text
alert tcp any any -> $HOME_NET any (
    msg:"TCP traffic observed";
    sid:1000001;
    rev:1;
)
```

This rule generates an alert for TCP traffic matching its header conditions. It is a basic example of rule syntax rather than a dedicated port-scan detection rule.

### Important Rule Options

- `msg`: defines the alert message.
- `sid`: identifies the rule.
- `rev`: specifies the rule revision.

`$HOME_NET` represents the protected network and should be configured appropriately in the Snort configuration.

### Rule File

Custom rules can be stored in a separate file, such as `/etc/snort/rules/local.rules`. The location is an example and can be changed to match the installation.

---

## Rule Actions

Snort supports several rule actions.

| Action  | Purpose |
|---------|---------|
| `alert` | Generates an alert |
| `log`   | Logs matching traffic |
| `pass`  | Allows matching traffic to pass |
| `drop`  | Drops matching traffic in an appropriate inline IPS configuration |
| `block` | Blocks the associated flow according to the configured operating mode |

> **Note:** The exact behavior depends on the Snort version, configuration, and operating mode.

### Alerting

An `alert` rule reports matching traffic. For example:

```text
alert tcp any any -> $HOME_NET any (
    msg:"TCP traffic observed";
    sid:1000001;
    rev:1;
)
```

This rule generates an alert but does not, by itself, block the connection.

### Blocking

Blocking requires an appropriate IPS configuration and a traffic path through which Snort can enforce the blocking action.

- A passive IDS deployment can inspect traffic and generate alerts without necessarily being able to prevent the connection.
- In an inline IPS deployment, a suitable blocking action can prevent matching traffic from passing through the inspection point.

> **Important:** Detection and prevention are separate functions. Both must be evaluated when implementing a scan-detection system.

---

## Network Scan Detection with Nmap

### Objective

Investigate whether Snort can identify scanning activity generated by Nmap.

### Testing Process

1. Start Snort with the intended configuration and detection rules.
2. Generate controlled scanning traffic using Nmap.
3. Examine Snort's alert output.
4. Compare the observations with packets captured using Wireshark.
5. Investigate whether the configured response generates alerts, blocks traffic, or performs both functions.
6. Repeat the test to evaluate the behavior.

### Understanding Scan Detection

A port scan may involve repeated connection attempts to different ports or hosts. A useful detection rule must identify traffic patterns relevant to the intended detection objective.

A rule that matches generic TCP traffic can generate alerts without distinguishing normal connections from port scanning. Detection quality therefore depends on the rule conditions, the traffic being observed, and the monitoring configuration.

---

## TCP Traffic Analysis

Wireshark can be used to examine TCP packets generated during network scans. The following TCP flags are useful when investigating connection behavior:

- SYN
- SYN-ACK
- ACK
- RST-ACK

A typical TCP three-way handshake consists of:

1. The client sends SYN.
2. The server responds with SYN-ACK.
3. The client sends ACK.

A SYN-ACK response commonly indicates that a TCP port is open and accepting connection attempts. A RST-ACK response commonly indicates that a TCP port is closed, depending on the packet context and scanning method.

> **Note:** These observations help explain TCP behavior but are not sufficient by themselves to identify every type of port scan.

---

## IDS and IPS

### Intrusion Detection System (IDS)

An IDS monitors network traffic and identifies activity that matches configured rules or suspicious patterns. Depending on its configuration, it can generate alerts for further investigation.

### Intrusion Prevention System (IPS)

An IPS can inspect traffic and apply preventive actions, such as dropping matching packets, when deployed and configured appropriately.

### Key Differences

| Feature                              | IDS            | IPS |
|--------------------------------------|----------------|-----|
| Monitors network traffic             | Yes            | Yes |
| Generates alerts                     | Yes            | Yes |
| Can prevent traffic from passing     | Not inherently | Yes, with suitable inline configuration |
| Requires appropriate rules           | Yes            | Yes |
| Requires suitable network visibility | Yes            | Yes |

Snort's effectiveness depends on its configuration, rule set, operating mode, and access to the relevant network traffic.

---

## Detection and Prevention Considerations

### Network Visibility

Snort must be able to observe the traffic being investigated. If the relevant packets do not reach the monitored interface, Snort cannot detect them through that interface.

### Rule Configuration

A rule only matches traffic that satisfies its conditions. Incorrect network variables, unsuitable rule conditions, or a mismatch between the rule and the observed traffic can prevent the intended detection.

### Alert Verification

An alert should be associated with the traffic being tested. The presence of an alert does not automatically establish that a complete scan was detected.

### Blocking Verification

Blocking must be evaluated separately from alerting. A suitable IPS configuration is required, and the network traffic path must allow Snort to enforce the intended action.

---

## Custom Rule Examples

The examples below are starting points for a controlled lab, not a guarantee of accurate scan classification. Test the alert-only rule first and tune the threshold for the lab traffic.

### Example 1: Alert on Repeated TCP SYN Packets

Save this rule in a custom rule file such as `local.rules`:

```text
alert tcp any any -> $HOME_NET any (
    msg:"Possible TCP SYN scan - repeated SYN packets";
    flags:S;
    flow:stateless;
    detection_filter:track by_src, count 20, seconds 10;
    sid:1000002;
    rev:1;
)
```

**How it works**

- `alert` generates an alert; it does not block traffic.
- `tcp` limits the rule to TCP traffic.
- `any any` matches any source address and source port.
- `$HOME_NET any` targets any port on the protected network defined in the Snort configuration.
- `flags:S` matches TCP packets with the SYN flag set.
- `flow:stateless` allows the rule to inspect packets without requiring an established TCP session.
- `detection_filter` counts matching packets by source IP and triggers an event after the configured rate threshold is exceeded.
- `sid` is the local rule identifier; `rev` is the revision number.

**Limitation:** Repeated SYN packets do not prove that a port scan is occurring. Normal applications, retries, or other traffic may trigger this rule. The threshold is an example and must be tuned.

### Example 2: Validate the Rule and Start Alerting

First, check the configuration:

```bash
sudo snort -T -c /etc/snort/snort.lua -R /etc/snort/rules/local.rules
```

Then listen on the interface connected to the authorized lab network:

```bash
sudo snort -c /etc/snort/snort.lua \\
  -R /etc/snort/rules/local.rules \\
  -i eth0 -A alert_fast
```

Replace `eth0` and the configuration/rule paths with the actual values on your system. Confirm that `$HOME_NET` in the configuration includes the lab target network. These commands assume Snort is installed directly on Linux; a container may use different paths and interface names.

### Example 3: Inspect a Saved Packet Capture

If a PCAP file was captured from an authorized lab, Snort can inspect it offline:

```bash
sudo snort -c /etc/snort/snort.lua \\
  -R /etc/snort/rules/local.rules \\
  -r ./lab-traffic.pcap -A alert_fast
```

This reads an existing capture file and evaluates its packets against the loaded rules. Replace `./lab-traffic.pcap` with the actual file path. Offline PCAP inspection can test detection logic, but it cannot demonstrate that live traffic was blocked.

### Example 4: Controlled Scan Test

Only run scans against a system you own or have explicit permission to test. From a separate lab machine, a limited TCP connect scan can be used to generate traffic:

```bash
nmap -sT -p 20-100 <LAB_TARGET_IP>
```

Replace `<LAB_TARGET_IP>` with the IP address of your own lab target. Keep the target and Snort sensor on a network path where the sensor can actually observe the traffic.

During the test:

1. Start Snort with the alert rule loaded.
2. Run the limited scan from the separate lab machine.
3. Review the Snort alert output.
4. Capture the same traffic in Wireshark if possible.
5. Compare timestamps, source/destination addresses, and TCP flags.
6. Record whether the rule triggered and whether unrelated traffic also matched.

A rule alert is evidence that its conditions matched; it is not, by itself, proof that every scan was detected.

### Example 5: Prevention Rule — Inline IPS Only

After the alert-only rule has been reviewed and tuned, the action can be changed to `drop` for a controlled inline IPS test:

```text
drop tcp any any -> $HOME_NET any (
    msg:"Possible TCP SYN scan - drop matching packets";
    flags:S;
    flow:stateless;
    detection_filter:track by_src, count 20, seconds 10;
    sid:1000003;
    rev:1;
)
```

**Important:** A `drop` action only prevents matching packets from passing when Snort is correctly configured in an inline IPS path that can enforce the action. Running Snort as a passive IDS or reading a PCAP file does not block the original live traffic. This example drops matching packets after the rate threshold is exceeded; it does not necessarily block the source IP for all protocols or all future traffic.

Do not switch to a blocking rule on a production network without an authorized test plan and a way to restore connectivity. Verify blocking separately from alert generation.

## Container Deployment Notes

A containerized Snort setup needs access to the relevant network traffic, the Snort configuration, and the custom rules. The exact image name, paths, interface, and startup command depend on how the container image was built.

Before starting the container:

1. Confirm the image contains Snort 3 and check its version.
2. Make the configuration and custom rules available inside the container, preferably as read-only mounts when they do not need to be changed at runtime.
3. Ensure the container can observe the lab traffic. A container on an ordinary isolated bridge network may not see traffic between other machines.
4. Grant only the network capabilities required by the selected capture or inline mode.
5. Start with alert-only monitoring and confirm visibility before attempting inline prevention.
6. Keep the test network isolated and avoid exposing the Snort management interface unnecessarily.

For a container, run the equivalent of the validation and listening commands from inside the container using paths and interface names that actually exist there. Do not copy a host interface name into the container command without checking it first.

## Troubleshooting Checklist

When Snort does not behave as expected, investigate the following areas:

- Confirm the installed Snort version.
- Check the configuration file path.
- Validate the configuration.
- Confirm that the intended rule file is loaded.
- Check rule syntax and identifiers.
- Verify the protected network configuration.
- Confirm that the selected interface can observe the relevant traffic.
- Examine alert output and available logs.
- Check whether Snort is operating in IDS or inline IPS mode.
- Verify the effect of blocking independently from alert generation.

Each change should be evaluated separately to make troubleshooting easier.

---

## Further Investigation

Potential areas for continued experimentation:

- Improving the accuracy of scan-detection rules.
- Investigating detection thresholds and repeated connection attempts.
- Examining false positives and missed detections.
- Comparing Snort alerts with Wireshark packet captures.
- Investigating inline IPS configuration.
- Exploring containerized deployment and network visibility.
- Documenting the relationship between detection rules, alerts, and blocking actions.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
