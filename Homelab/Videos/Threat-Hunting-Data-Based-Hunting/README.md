# Threat Hunting — Data-Based Hunting (DBH)

## Video Information

- **Topic:** Data-Based Hunting, worked example: hunting in process creation logs (Windows Event ID 4688)
- **Creator / Channel:** Instructor-provided video (caption: "Threat Hunting #PTH #Windows #Event #ID")
- **Source URL:** Not recorded in these notes
- **Date Studied:** 2026-11-08 (from the video transcript)

## Overview

These notes summarize a lesson on Data-Based Hunting, a threat hunting approach that starts from a data source and asks whether anything in it looks malicious. The example uses Windows Event ID 4688 (a new process has been created), which records process execution.

## Key Topics

- ABH and DBH reach the same place from opposite directions. ABH goes from an attack to relationships to behaviors; DBH starts from the behaviors in the data and builds up to relationships.
- DBH depends on understanding the data source and on knowing many attacks and how they appear in it.
- Broad question for the data source: does anything in these logs look malicious?
- The attack categories visible in process creation logs: malicious binaries, malicious documents (seen through the processes the opening application spawns), malicious use of legitimate tools, and masquerading as legitimate processes.
- Attackers can clear or modify logs, but evidence often remains.

## ABH vs DBH

| | ABH | DBH |
|---|---|---|
| Starting point | A specific attack | A specific data source |
| Main question | Did this attack happen in my network? | Does anything in this data look malicious? |
| Knowledge needed | Deep knowledge of one attack | Knowledge of many attacks and of the data source |
| For beginners | Simpler, more linear | Needs more experience, but has quick wins |

## Event ID 4688 Fields of Interest

- **New Process Name:** full path and name of the executed file
- **Creator Process:** the parent process that started it
- **Account Name:** the account the process ran under
- **Timestamp:** when it was executed

Note: a log entry only represents what happened. A process named `chrome.exe` is not necessarily the real Chrome.

## Five Hunting Techniques from the Lesson

1. **Process name anomalies.** Generic names (such as `update.exe`), names mimicking legitimate processes, random-looking names, and rare processes. Technique: aggregate events by unique process name, sort by least common, and build a whitelist over time.
2. **Unusual parent-child relationships.** For example an Office application spawning PowerShell is suspicious, while Explorer spawning Chrome is normal. Technique: focus on commonly exploited parents (Office, browsers, `runas`/`cmd`) and aggregate their child processes.
3. **Unusual process path.** Programs normally run from predictable locations (system directories, Program Files, user profile). Technique: aggregate by path on smaller, high-priority host groups. Example from the lesson: Windows Defender running from a user's profile directory instead of Program Files. The path may need to be split from the file name (tokenization) depending on the tool.
4. **Unusual execution time.** A process, user or system active outside its normal hours. Technique: build a baseline and compare using standard deviation or a simple comparison. Expect more false positives, such as scheduled tasks, backups and updates.
5. **Process never executed by this user before.** Technique: aggregate by user and process, focusing on sensitive users, users with a history of infections, and administrators rather than the whole network.

## Personal Notes

- Start small: pick a subset of hosts or a high-priority network segment before running these across the whole network.
- The first runs are noisy. Refine the query and keep a whitelist.
- Findings are candidates for investigation; context from the user and host decides.
- The lesson mentions five evidence realms as a way to build knowledge of data sources: friendly intelligence, threat intelligence, host, network and memory. The exact naming should be verified against the course material.
- DBH findings can later become ABH hunts or automated detections.

## Commands and Examples

The lesson shows event examples and aggregation tables (for example parent-child counts and process paths) rather than a fixed command set. No commands from this lesson have been personally tested yet.

## Practical Experiments

These notes are based on educational video content. No independent lab work is claimed here yet.

Planned follow-up:

- Enable process creation auditing (with command line) in a Windows VM and inspect 4688 events; compare with Sysmon event 1.
- Look at the Linux equivalent using `auditd` (`execve` records, `aureport -x --summary`) in a Linux VM.

## Questions and Follow-up

- What if process creation auditing (4688) is not enabled, or the log was cleared?
- What is the best way to build and maintain a whitelist without hiding real threats?
- Which parent processes are the most useful to monitor in a small environment?

## References

- [Microsoft — 4688(S): A new process has been created](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4688)
- [MITRE ATT&CK](https://attack.mitre.org/)

---

Part of My-Note. Personal technical knowledge base, continuously updated.
