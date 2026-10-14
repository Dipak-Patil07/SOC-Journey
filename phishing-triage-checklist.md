# Phishing Triage Checklist

## 1. Email
- [ ] Sender address and display name checked
- [ ] `Return-Path` / `Reply-To` match?
- [ ] SPF / DKIM / DMARC results reviewed
- [ ] `Received` chain traced, originating IP noted
- [ ] Subject/body: urgency, threats, generic greeting, odd grammar

## 2. Links
- [ ] Real destination compared with visible text
- [ ] URL defanged before sharing
- [ ] Scanned (URLScan / VirusTotal), redirects noted
- [ ] Domain age and registrar checked (WHOIS)

## 3. Attachments
- [ ] Hash calculated and checked on VirusTotal
- [ ] File type matches extension
- [ ] Sandboxed, behaviour recorded

## 4. Scope
- [ ] Same sender/subject/URL searched across mailboxes
- [ ] Proxy/DNS logs checked for clicks
- [ ] Users who submitted credentials identified

## 5. Response
- [ ] Indicators blocked
- [ ] Emails purged
- [ ] Credentials reset, sessions revoked
- [ ] Ticket documented with evidence and classification
