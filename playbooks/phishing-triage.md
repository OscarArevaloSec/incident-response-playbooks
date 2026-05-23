# Phishing Email Triage Playbook

## Scenario

A user reports a suspicious email, or an email security tool generates an alert. The message may contain a suspicious link, attachment, impersonation attempt, credential-harvesting page, payment fraud request, or malware delivery attempt.

## Objective

The objective is to determine whether the email is benign, spam, phishing, business email compromise, credential harvesting, or malware-related. The analyst should identify indicators, assess user impact, recommend containment, and document findings clearly.

## Initial Triage

| Question | Evidence to Review | Notes |
|---|---|---|
| Who reported the email? | Reporter, mailbox, department, role. | Prioritize finance, HR, executives, IT, and privileged users. |
| Who sent it? | Display name, envelope sender, reply-to, return-path, sending domain. | Display name alone is not reliable. |
| What is the lure? | Invoice, password reset, MFA alert, shared document, urgent request, job offer. | The lure helps classify intent. |
| Are there links? | URLs, redirects, shortened links, domains, query strings. | Do not click live links from a production workstation. |
| Are there attachments? | Filename, extension, hash, macro presence, archive contents. | Handle files in a safe analysis environment only. |
| Did the user interact? | Clicked link, opened attachment, entered credentials, replied, forwarded. | User interaction changes severity and containment. |
| Was it sent to others? | Message trace, email gateway logs, similar subjects/senders. | Determines scope and purge requirement. |

## Header and Sender Review

| Field | What to Check |
|---|---|
| From | Display name spoofing, lookalike domain, unexpected sender. |
| Reply-To | Different reply address or suspicious external mailbox. |
| Return-Path | Bounce address mismatch or suspicious domain. |
| Received headers | Sending infrastructure, relay chain, suspicious originating IP. |
| SPF/DKIM/DMARC | Pass, fail, softfail, alignment, and policy results. |
| Message-ID | Domain mismatch or malformed identifiers. |

## Link and Attachment Review

| Indicator | Triage Method |
|---|---|
| URLs | Defang URLs, extract domains, check reputation, review redirect chains safely. |
| Domains | Check age, typosquatting, brand impersonation, unusual TLDs, DNS records. |
| Attachments | Record filename, extension, hash, file type, and sandbox result if available. |
| QR codes | Treat as URLs; decode safely and inspect target domain. |
| Office documents | Check macro presence, external template links, and suspicious embedded content. |

## Investigation Steps

| Step | Analyst Action | Expected Output |
|---|---|---|
| 1 | Preserve the original email or headers. | Evidence retained for analysis. |
| 2 | Identify sender, recipients, subject, timestamp, links, and attachments. | Core email metadata documented. |
| 3 | Extract and defang IOCs. | Safe IOC list ready for investigation. |
| 4 | Check authentication results and sender reputation. | Sender legitimacy assessed. |
| 5 | Determine whether any user clicked, replied, downloaded, or submitted credentials. | Impact and urgency assessed. |
| 6 | Search for similar messages across the environment. | Scope documented. |
| 7 | Recommend containment such as message purge, domain block, password reset, or endpoint review. | Actionable response plan. |
| 8 | Document classification and lessons learned. | Report ready for ticket closure or escalation. |

## Classification Guidance

| Classification | Indicators |
|---|---|
| Benign | Expected sender, valid authentication, no suspicious lure, business context confirmed. |
| Spam | Unwanted bulk message with no targeted credential, malware, or fraud intent. |
| Phishing | Credential lure, suspicious link, impersonation, fake login page, or security-themed urgency. |
| Business email compromise | Payment change, gift card request, invoice fraud, executive impersonation, or vendor impersonation. |
| Malware delivery | Suspicious attachment, macro-enabled file, script, archive, executable, or known malicious hash. |

## Containment Options

Containment may include purging the message, blocking sender/domain/URL, resetting credentials for affected users, revoking sessions, reviewing MFA activity, isolating endpoints, and notifying users who received the message.

## IOC Collection Table

| Type | Indicator | Defanged Value | Context | Action |
|---|---|---|---|---|
| URL |  |  | Link in email body |  |
| Domain |  |  | Sender or landing page |  |
| IP Address |  |  | Header or URL resolution |  |
| Hash |  |  | Attachment |  |
| Email |  |  | Sender or reply-to |  |

## Analyst Notes

A good phishing investigation is not just about finding a bad link. It is about determining delivery, user interaction, scope, and containment. The final report should make it easy for another analyst or manager to understand what happened and what should happen next.
