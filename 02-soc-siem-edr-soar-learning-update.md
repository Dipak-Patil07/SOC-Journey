# SOC Analyst Learning Update — SIEM, EDR, SOAR & Log Analysis

## Overview

Guys i'm telling you, Over the past two weeks, I continued building my SOC Analyst foundation through hands-on security labs and learning modules on TryHackMe.

This phase focused on understanding how modern Security Operations Centers collect, investigate, and respond to security events using **SIEM, EDR, log-analysis platforms, and SOAR**.

Rather than treating these tools as isolated technologies, I focused on understanding where each fits into the SOC workflow.

---

## Modules Completed

### 1. Introduction to EDR

**Focus:** Endpoint Detection and Response

Key areas covered:

- Fundamentals of EDR
- Endpoint telemetry and visibility
- Detection of suspicious endpoint activity
- Investigation and response concepts
- Role of EDR in a SOC environment

**SOC takeaway:**  
EDR provides visibility into endpoint activity and helps analysts investigate suspicious processes, files, network connections, and other endpoint events.

---

### 2. Introduction to SIEM

**Focus:** Security Information and Event Management

Key areas covered:

- SIEM fundamentals
- Centralised security logging
- Event collection and analysis
- Security monitoring concepts
- How SIEM supports SOC investigations

**SOC takeaway:**  
A SIEM gives analysts a central place to search and correlate security events from different systems, making it easier to investigate alerts and identify patterns.

---

### 3. Splunk: The Basics

**Focus:** Log investigation using Splunk

Key areas covered:

- Splunk fundamentals
- Searching security logs
- Investigating events
- Understanding how SOC analysts use Splunk during investigations
- Using log data to support alert analysis

**SOC takeaway:**  
A SOC analyst needs to be comfortable moving from an alert to the underlying log evidence. Splunk provides a practical environment for searching and investigating that data.

---

### 4. Elastic Stack: The Basics

**Focus:** Log investigation using the Elastic Stack

Key areas covered:

- Elastic Stack fundamentals
- Security log investigation
- Searching and analysing collected events
- Understanding how Elastic can support SOC workflows

**SOC takeaway:**  
Elastic provides another common ecosystem for collecting, searching, and analysing security telemetry. Learning more than one platform helps build transferable log-analysis skills.

---

### 5. Introduction to SOAR

**Focus:** Security Orchestration, Automation and Response

Key areas covered:

- SOAR fundamentals
- Security orchestration
- Security automation
- Incident-response workflows
- How automation can reduce repetitive analyst tasks

**SOC takeaway:**  
SOAR can connect security tools and automate repeatable response actions, allowing analysts to spend more time on investigations that require human judgement.

---

## How These Technologies Fit Together

A simplified SOC workflow can look like:

```text
                    Security Events
                          |
                          v
              +-----------------------+
              |   SIEM / Log Platform |
              +-----------------------+
                          |
                          v
                    Alert / Detection
                          |
                          v
              +-----------------------+
              |     Analyst Triage    |
              +-----------------------+
                          |
              +-----------+-----------+
              |                       |
              v                       v
        Endpoint Evidence       Additional Logs
              |                       |
              +-----------+-----------+
                          |
                          v
                    Investigation
                          |
                          v
                  Response Decision
                          |
                          v
                    SOAR / Automation
```

This helped me understand that **SIEM, EDR, and SOAR are complementary parts of a SOC workflow rather than interchangeable tools**.

---

## Skills Developed

Through these modules, I strengthened my understanding of:

- SOC monitoring concepts
- SIEM fundamentals
- EDR fundamentals
- Log investigation
- Security event analysis
- Splunk fundamentals
- Elastic Stack fundamentals
- Security orchestration
- Security automation
- Incident-response concepts
- Alert investigation workflow

---

## What I Learned

One of the main takeaways from this stage is that SOC analysis is not simply about looking at an alert and deciding whether it is malicious.

A useful investigation requires connecting the alert with supporting evidence:

```text
Alert
  ↓
Understand the detection
  ↓
Identify the affected asset/user
  ↓
Examine relevant logs
  ↓
Check endpoint activity
  ↓
Look for related events
  ↓
Determine whether the activity is suspicious
  ↓
Document findings
  ↓
Escalate or respond
```

This is the workflow I am continuing to build toward as I progress through more SOC-focused labs.

---

## Current Learning Progress

**Completed recently:**

- [x] Introduction to EDR
- [x] Introduction to SIEM
- [x] Splunk: The Basics
- [x] Elastic Stack: The Basics
- [x] Introduction to SOAR

**Previous documented work:**

- [x] SOC L1 Alert Triage

---

## Next Focus

My next focus is to move beyond introductory concepts and spend more time on **actual alert investigation, log analysis, detection logic, incident investigation, and SOC case scenarios**.

The goal is to build a portfolio that demonstrates not only knowledge of security tools, but also the ability to reason through a security alert and document an investigation clearly.

---

### Platform

**TryHackMe — SOC Analyst learning path**

This document represents my learning notes and understanding of the concepts covered. It is not intended to reproduce TryHackMe course material or solutions.
