# 05: Phishing Analysis

## Common types
- **Phishing:** mass emails impersonating a trusted brand
- **Spear phishing:** targeted at a specific person or team
- **Whaling:** targets senior executives
- **Smishing / vishing:** SMS and voice variants
- **Business Email Compromise (BEC):** impersonating an executive or vendor to request payments

## Email header analysis
| Header | Why it matters |
|--------|----------------|
| `From` | Display name can be faked; check the actual address and domain |
| `Return-Path` / `Reply-To` | A mismatch with `From` is a red flag |
| `Received` | Read bottom to top to trace the mail's path and originating server |
| `Message-ID` | Domain often doesn't match the claimed sender |
| `Authentication-Results` | **SPF, DKIM, DMARC** pass/fail results |
| `X-Originating-IP` | Possible true sender IP |

**SPF** checks the sending server is authorised for the domain. **DKIM** verifies a cryptographic signature. **DMARC** tells receivers what to do when SPF/DKIM alignment fails.

## Body and link analysis
- Urgency, threats, or too-good-to-be-true offers
- Generic greetings, spelling errors, mismatched branding
- **Hover over links** and compare the visible text with the real destination
- Look-alike domains (typosquatting, extra subdomains, unusual TLDs)
- Check tracking pixels and per-recipient URLs

## Attachment analysis
1. Don't open on a real machine, use an isolated VM or sandbox.
2. Hash it (`sha256sum`) and look the hash up on VirusTotal.
3. Check file type vs. extension; watch for macros, scripts, archives.
4. Detonate in a sandbox (e.g. ANY.RUN, Hybrid Analysis) and note network and process behaviour.

## Investigating a suspicious URL
- **Defang** before sharing: `hxxps://example[.]com`
- Scan with URLScan / VirusTotal (screenshot, redirects, hosting IP)
- WHOIS: registration date, registrar (newly registered domains are suspicious)
- Browse only inside an isolated environment
- Try walking up the directory path to see if there's an open directory with a kit or logs

## Analysing a phishing kit
A phishing kit is the packaged set of files (HTML, CSS, PHP) that powers a fake login page.
- Hash the archive and look it up on VirusTotal for first-seen dates
- Read the PHP: find where captured credentials are **sent** (email addresses, Telegram bots, log files)
- Look for reused infrastructure to link multiple campaigns

## Response actions
- Block sender domain and URLs at the mail gateway/proxy
- Search mailboxes for the same message and purge
- Check proxy/DNS logs for users who clicked
- Reset credentials and revoke sessions for anyone who submitted data
- Report the domain to the registrar/host and brand owner
- Feed IOCs to threat intel / SIEM detection rules

See also: [templates/phishing-triage-checklist.md](templates/phishing-triage-checklist.md)
