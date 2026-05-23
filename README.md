# Incident Response Playbooks

This repository contains blue-team triage playbooks, incident documentation templates, and SOC-style investigation workflows. The goal is to demonstrate practical thinking for entry-level SOC Analyst, Security Operations Analyst, Cybersecurity Analyst, and Junior Incident Response Analyst roles.

The playbooks are written for learning and portfolio demonstration. They do not represent confidential employer procedures and should be adapted to the tooling, authority, escalation paths, and legal requirements of a real organization.

## Playbook Index

| Playbook | Incident Type | Primary Skills Demonstrated | Status |
|---|---|---|---|
| [Phishing Triage](playbooks/phishing-triage.md) | Reported suspicious email | Header review, URL inspection, IOC collection, user impact assessment, escalation. | Drafted |
| [Suspicious Login](playbooks/suspicious-login.md) | Authentication alert | Log review, source IP analysis, account impact, containment decisions. | Drafted |
| [Malware Alert](playbooks/malware-alert.md) | Endpoint or EDR alert | Triage, host isolation logic, hash review, evidence collection, escalation. | Drafted |

## Templates

| Template | Purpose |
|---|---|
| [Incident Report Template](templates/incident-report-template.md) | Reusable structure for documenting alert investigations and security incidents. |
| [IOC Collection Template](templates/ioc-collection-template.md) | Structured table for collecting IP addresses, domains, URLs, hashes, file paths, CVEs, and related context. |

## Playbook Method

Each playbook follows a consistent analyst workflow: detection, triage, investigation, containment, eradication and recovery, escalation, documentation, and lessons learned. This structure is intentionally simple because a useful playbook should help an analyst make better decisions under pressure.

## Portfolio Intent

These documents are designed to show how I think through alerts. They emphasize evidence, assumptions, severity, business impact, and clear recommendations rather than tool screenshots alone.

## Safety and Ethics

Do not use these playbooks as authorization to investigate systems you do not own or administer. In a real environment, follow company policy, legal guidance, chain-of-custody requirements, and the approved escalation process.
