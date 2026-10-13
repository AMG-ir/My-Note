# IDS vs. IPS

- **Category:** Network Security
- **Status:** Research Notes
- **Type:** Conceptual Research

## Research Question

What is the difference between an Intrusion Detection System (IDS) and an Intrusion Prevention System (IPS)?

## Purpose

To understand how IDS and IPS monitor network activity, identify suspicious traffic, and differ in their response to potential threats.

## Background

IDS and IPS technologies analyze system or network activity to identify signs of possible security incidents. They can use detection methods such as signatures, protocol analysis, and behavioral indicators. Their exact capabilities depend on the product and its configuration.

## Key Findings

### Intrusion Detection System (IDS)

An IDS monitors events or network traffic and reports activity that may be suspicious or malicious.

- Detects and generates alerts about potential threats.
- A network IDS commonly monitors a copy of traffic, so it can observe activity without directly sitting in the traffic path.
- By itself, an IDS generally does not block the original traffic automatically.
- An administrator or another security control may need to respond to an alert.

### Intrusion Prevention System (IPS)

An IPS performs detection and can also take action to prevent or limit suspicious traffic.

- Inspects network traffic for potential threats.
- A network IPS is commonly deployed inline, in the path of the traffic it inspects.
- Depending on its rules and configuration, it can drop packets, block traffic, or take other configured actions.
- Because it can affect traffic flow, incorrect rules or false positives may interrupt legitimate connections.

## Main Differences

| Feature | IDS | IPS |
|---|---|---|
| Full name | Intrusion Detection System | Intrusion Prevention System |
| Main purpose | Detect and alert | Detect and help prevent |
| Typical network placement | Often monitors a copy of traffic | Often placed inline with traffic |
| Automatic blocking | Usually not by itself | Can block or drop traffic when configured |
| Impact on traffic flow | Typically does not directly interrupt forwarded traffic | May affect traffic flow |
| Main operational concern | Alerts need to be reviewed and acted upon | Prevention rules must be tuned to avoid blocking legitimate traffic |

These are common deployment patterns, not absolute rules. Some products support both IDS and IPS modes, and features vary by implementation.

## Example

Imagine a monitoring system observes a port scan against a server:

- **IDS mode:** It detects a matching pattern and generates an alert for the administrator.
- **IPS mode:** If configured with an appropriate prevention rule and deployed to inspect the traffic inline, it may drop matching packets or block the traffic.

Detection and prevention depend on the product, rules, traffic visibility, and configuration. An alert alone does not guarantee that traffic was blocked.

## Advantages and Limitations

### IDS

**Advantages**
- Provides visibility into suspicious network activity.
- Can monitor copied traffic without directly affecting the traffic path.
- Helps administrators investigate events and tune defenses.

**Limitations**
- An alert does not itself stop the activity.
- Alerts require review and may include false positives.
- Visibility depends on where and how traffic is monitored.

### IPS

**Advantages**
- Can automatically block traffic that matches configured prevention rules.
- May reduce the time between detecting and responding to a threat.

**Limitations**
- Incorrect rules or false positives can block legitimate traffic.
- Inline deployment introduces an additional consideration for availability and traffic flow.
- Rules and detection content need ongoing maintenance.

## Relationship to Snort

Snort can be used for network intrusion detection and, when configured and deployed in a supported inline prevention setup, intrusion prevention. The operating mode, configuration, and traffic path determine whether it only alerts or can also take prevention actions.

Related lab: [Network Monitoring](../../Labs/Network-Monitoring/README.md) and [Snort 3 Network Scan Detection](../../Labs/Network-Monitoring/Snort-3/).

## Practical Verification

These notes document conceptual learning from research. They do not claim that an IDS or IPS deployment was independently configured or tested as part of this research note. Related traffic observation and firewall experiments are documented in the Network Monitoring lab.

## Conclusion

The central difference is that an IDS focuses on detecting and reporting possible threats, while an IPS includes prevention capabilities and can take configured actions against suspicious traffic. Both are useful defensive technologies, and their effectiveness depends on suitable placement, accurate rules, and ongoing monitoring.

## References

- [NIST: Guide to Intrusion Detection and Prevention Systems (IDPS)](https://www.nist.gov/publications/guide-intrusion-detection-and-prevention-systems-idps)
- [NIST: Intrusion Detection and Prevention Systems](https://csrc.nist.gov/pubs/book-section/2010/10/intrusion-detection-and-prevention-systems/final)
- [Cisco: Intrusion Prevention System — IDS and IPS modes](https://www.cisco.com/content/en/us/td/docs/routers/sdwan/configuration/security/ios-xe-16/security-book-xe/intrusion-prevention.pdf)

---

Part of My-Note. Personal technical knowledge base, continuously updated.
