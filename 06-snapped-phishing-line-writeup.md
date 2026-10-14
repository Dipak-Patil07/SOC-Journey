# 06: Lab Write-up: Snapped Phish-ing Line

**Platform:** TryHackMe | **Difficulty:** Easy | **Category:** Phishing analysis

## Scenario
A phishing campaign targeted several employees. Using the supplied emails, I had to trace the campaign back to the attacker's infrastructure, retrieve the phishing kit, and analyse it. All artifacts were handled only inside the provided isolated VM, since the kit came from a real campaign.

## Approach

### 1. Email triage
- Opened each sample in the `phish-emails` folder and compared headers and bodies.
- Identified the **sender address** used across the campaign.
- Located the **per-recipient redirect link** in each email. Each victim received a unique URL, which lets the attacker track who clicked.

### 2. Following the link
- Visited the URL inside the VM's browser and observed the fake login page.
- Walked back up the URL path one directory at a time and found an **exposed directory** containing the phishing kit archive.

### 3. Analysing the kit archive
- Downloaded the archive and generated its hash with `sha256sum`.
- Searched the hash on **VirusTotal** to find when the kit was first submitted.
- Looked up the hosting domain on VirusTotal/WHOIS to see its **registration date**. A recently registered domain is typical of throwaway phishing infrastructure.

### 4. Reading the kit
- Unzipped the archive and reviewed the PHP files.
- Found where harvested credentials were being **emailed to the attacker**, and identified additional attacker addresses hard-coded in the kit.
- Found a **log file** on the same host holding details of victims who submitted data, which is evidence of real impact.

## IOC table
*(Fill in with your own findings, defanged.)*

| Type | Value | Notes |
|------|-------|-------|
| Sender email | `...` | Used across the campaign |
| Phishing URL | `hxxp://...` | Per-recipient redirect |
| Kit archive URL | `hxxp://...` | Exposed in open directory |
| SHA256 | `...` | Kit archive |
| Domain | `...` | Registered on `YYYY-MM-DD` |
| Attacker emails | `...` | Found in kit PHP |

## Framework mapping
- **Kill Chain:** Delivery (email), Exploitation (user submits credentials)
- **ATT&CK:** T1566.002 Spearphishing Link, T1589 Gather Victim Identity Information (credential harvesting)

## Recommendations
1. Block the sender, domain and URLs.
2. Search for and purge the same email across all mailboxes.
3. Identify affected users from logs, then force password resets and revoke sessions.
4. Enable/enforce MFA and strengthen SPF/DKIM/DMARC checking.
5. Run user awareness training on link inspection.

## What I learned
- Walking up a URL path can expose attacker mistakes like open directories.
- Kit source code reveals where stolen data goes, which is a strong pivot point.
- Domain age and first-seen dates help build a campaign timeline.

## Screenshots
*(Add your own, redacting anything sensitive, e.g. `images/header-analysis.png`.)*
