# Incident Response Playbooks

Blue-team triage playbooks for common security incidents. Designed to demonstrate SOC analyst readiness and structured incident response thinking.

## Playbooks

| Playbook | Incident Type | Status |
|---|---|---|
| `phishing-triage.md` | Reported phishing email triage | Planned |
| `suspicious-login.md` | Suspicious authentication alert | Planned |
| `malware-alert.md` | Malware detection and containment | Planned |
| `data-exfiltration.md` | Potential data exfiltration alert | Planned |

## Templates

| Template | Purpose |
|---|---|
| `incident-report-template.md` | Reusable incident report structure |
| `ioc-collection-template.md` | Indicators of compromise collection sheet |

## Playbook Structure

Each playbook follows this structure:

1. **Detection** — What triggered the alert and initial indicators
2. **Triage** — Initial assessment steps and priority determination
3. **Investigation** — Evidence collection and analysis steps
4. **Containment** — Immediate actions to limit impact
5. **Eradication & Recovery** — Remediation steps
6. **Lessons Learned** — Post-incident documentation

## Purpose

These playbooks are designed for learning and portfolio demonstration. They reflect real-world SOC workflows adapted from industry frameworks including NIST SP 800-61 and SANS incident response methodology.
