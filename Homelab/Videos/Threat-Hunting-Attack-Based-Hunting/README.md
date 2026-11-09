# Threat Hunting — Attack-Based Hunting (ABH)

## Video Information

- **Topic:** Attack-Based Hunting, worked example: hunting for malicious local account creation
- **Creator / Channel:** Instructor-provided video (caption: "Threat Hunting #PTH #Windows #Event #ID")
- **Source URL:** Not recorded in these notes
- **Date Studied:** 2026-11-08 (from the video transcript)

## Overview

These notes summarize a lesson on Attack-Based Hunting, a threat hunting approach that starts from a specific attack and works toward the evidence it leaves behind. The lesson walks through one example: an attacker creating a local administrator account after compromising a host.

## Key Topics

- An attack can be viewed as an unwanted **relationship** between an attacker and a user or system. Each relationship shows up as an **observable behavior**, and each behavior leaves **evidence** (logs, packet captures, files).
- Starting from a real report: a US-CERT alert (TA18-074A) about Russian government activity against energy and other critical infrastructure.
- Placing the attack in a wider classification with **MITRE ATT&CK**: technique *Create Account* (T1136), under the *Persistence* tactic.
- Hunting for **anomalies**, not for every account creation, because creating accounts is normal in most networks.
- The three questions asked for every behavior (see below).

## The Three ABH Questions

1. What am I looking for?
2. Where will I find it (which log, which event)?
3. How can I manipulate the data to see it (search, filter, aggregate, statistics)?

## Relationships in the Example

For a malicious local account to exist, a chain of events must have happened:

1. An attacker gained unauthorized access to a system.
2. A user-management tool was executed on the host.
3. A new local account was created.

## Anomalies and Where They Appear (Windows)

| Anomaly | Event / source | Approach |
|---------|----------------|----------|
| Account name does not match the naming convention | 4720 (account created) | Search account creation events and inspect usernames |
| Account created with unexpected or insecure properties (e.g. password never expires) | 4738 (account changed) | Only look at 4738 events directly after a 4720; compare fields with the organization's template |
| Account immediately added to a privileged group | 4732 (member added to group) | Correlate 4732 within about a minute after 4720 |
| Account created at an unusual time for the creating user | 4720 plus logon/logoff events (4624 / 4634) | Compare with the user's normal activity hours; standard deviation or a simple comparison |
| Local account created on a domain member | 4720 | Separate `DOMAIN\user` accounts from local accounts; depends on where logs are collected |
| Account created by a user who has never created one | 4720 | Aggregate by creating user and look at the least common |
| Account created from a system that has never created one | 4720 | Aggregate by source system and look at the least common |

The lesson stresses that this list is not complete; other anomalies are possible.

## Personal Notes

- ABH is a good starting point because it focuses on one attack at a time.
- It requires knowing both the attack and how it appears in the available evidence sources.
- A single hunting finding is a candidate for investigation, not proof. Context (who, when, from which system) decides.
- Local logs can be cleared by an attacker. Logs should be forwarded to a central place (SIEM or a separate log server) soon after they are created, and the completeness of that forwarding matters too.
- Clearing a Windows log itself creates an event (1102 for Security, 104 for System).

## Commands and Examples

The lesson shows event examples and aggregation charts (creators of accounts, source systems) rather than a fixed command set. No commands from this lesson have been personally tested yet.

## Practical Experiments

These notes are based on educational video content. No independent lab work is claimed here yet.

Planned follow-up:

- Create test accounts in a Windows VM and inspect events 4720, 4738 and 4732 in Event Viewer.
- Look for the Linux equivalents (`auth.log` / `secure` and `auditd` records such as ADD_USER) and test them in a Linux VM.

## Questions and Follow-up

- How reliable is standard-deviation-based timing when a user works shifts or irregular hours?
- What is the minimum log-forwarding setup when no SIEM is available (for example Windows Event Forwarding or a separate syslog server)?
- How can missing or delayed logs from a host be detected?

## References

- [MITRE ATT&CK — Create Account (T1136)](https://attack.mitre.org/techniques/T1136/)
- US-CERT Alert TA18-074A (Russian government cyber activity targeting energy and other critical infrastructure sectors)

---

Part of My-Note. Personal technical knowledge base, continuously updated.
