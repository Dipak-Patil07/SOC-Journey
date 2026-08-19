# SOC L1 Alert Triage

> Notes from TryHackMe's SAL1 path — "SOC L1 Alert Triage" room.
> Completed as part of my Security Analyst Level 1 (SAL1) learning journey.

## What is Alert Triage?

Alert triage is the process a SOC (Security Operations Center) analyst uses to
quickly review incoming security alerts and decide **what matters, what
doesn't, and what needs to happen next.** A SOC can receive hundreds or
thousands of alerts a day from tools like SIEMs, IDS/IPS, EDR, and firewalls —
most analysts don't have time to investigate every single one in full depth,
so triage is the filtering step that makes the workload manageable.

The goal is simple: **separate real threats from noise, fast, without missing
something critical.**

## Why Triage Matters

- Analysts are flooded with alerts (a phenomenon called **alert fatigue**)
- Not every alert is malicious — many are false positives or expected behavior
- A missed real alert buried in noise can lead to a serious breach going undetected
- Speed matters: the longer an actual threat goes unnoticed, the more damage it can do

## Key Steps in the Triage Process

1. **Initial Review**
   - Read the alert details: source, destination, timestamp, alert type, severity
   - Check what triggered it (a rule, a signature, an anomaly, a threshold)

2. **Context Gathering**
   - Is this asset/user normally active at this time?
   - Is the IP/domain involved known-malicious, or internal and expected?
   - Has this alert type fired before for this asset? Is it recurring?

3. **Severity & Priority Assessment**
   - Not all alerts are equal — a failed login attempt is very different from
     a detected outbound connection to a known C2 (command and control) server
   - Common priority factors: asset criticality, potential impact, confidence
     of detection, and whether it fits a known attack pattern

4. **Decision: Escalate, Investigate Further, or Close**
   - **False positive** → document and close (with a reason)
   - **Needs more info** → investigate further (logs, endpoint data, network traffic)
   - **Confirmed or likely threat** → escalate to L2/incident response with
     clear, concise reporting

## Common Alert Sources Seen in Triage

| Source            | Example Alert                         |
|--------------------|----------------------------------------|
| SIEM               | Multiple failed logins from one IP     |
| EDR                | Suspicious process spawning (e.g. PowerShell from Word) |
| IDS/IPS            | Signature match for known exploit traffic |
| Firewall           | Unusual outbound connection to rare port |
| Email security gateway | Phishing attempt flagged            |

## What Makes a "Good" Triage Decision

- **Fast, but not careless** — quick doesn't mean skipping context
- **Documented** — every decision (even "closed as false positive") should
  have a clear reason, so the next analyst (or an auditor) understands why
- **Consistent** — using the same criteria across similar alerts avoids bias
  or missed patterns

## Key Takeaway

Alert triage is essentially **structured decision-making under time
pressure**. A SOC L1 analyst isn't expected to solve every case alone — their
job is to correctly sort the noise from the signal and hand off real threats
to the right people, quickly and with enough context that L2/IR can act
without starting from zero.

---
*Next up: SOC L1 Alert Reporting — how to properly document and communicate
high-risk alerts once triaged.*
