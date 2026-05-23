# Suspicious Login Triage Playbook

## Scenario

A security tool, help desk ticket, or system log indicates suspicious authentication activity. Examples include repeated failed logins, a successful login after many failures, impossible travel, a login from an unusual country, access outside normal work hours, or a privileged account logging in from an unfamiliar device.

## Objective

The objective is to determine whether the activity is benign, suspicious, or confirmed malicious. The analyst should identify the affected account, source, timeline, authentication outcome, potential impact, and recommended containment steps.

## Initial Triage

| Question | Evidence to Review | Notes |
|---|---|---|
| Which account was involved? | Username, user ID, email address, privilege level. | Prioritize privileged, service, and executive accounts. |
| What happened? | Failed login, successful login, MFA failure, password reset, new device, or location change. | Separate failed attempts from confirmed access. |
| When did it happen? | Timestamps in UTC and local time. | Build a short timeline before drawing conclusions. |
| Where did it come from? | Source IP, hostname, ASN, geolocation, VPN status. | Geolocation alone is not proof, but it can add context. |
| Was MFA involved? | MFA prompts, denials, approvals, bypasses, or enrollment changes. | MFA approval after repeated prompts may indicate fatigue attack risk. |
| What was accessed afterward? | VPN logs, endpoint logs, email logs, cloud logs, file access, admin actions. | Post-authentication behavior matters more than login alone. |

## Data Sources

| Source | Example Evidence |
|---|---|
| Linux authentication logs | `/var/log/auth.log`, `/var/log/secure`, `journalctl`, SSH daemon logs. |
| Windows logs | Security Event IDs such as 4624, 4625, 4634, 4648, 4672, and 4776. |
| Identity provider | Azure AD, Okta, Duo, Google Workspace, or other identity logs. |
| VPN or remote access | Successful sessions, failed attempts, device posture, source IP. |
| Endpoint telemetry | New process execution, suspicious command history, unusual parent-child processes. |
| Network telemetry | Connections after login, unusual destinations, large transfers, known bad IPs. |

## Investigation Steps

| Step | Analyst Action | Expected Output |
|---|---|---|
| 1 | Confirm the alert details and affected account. | A single account or set of accounts identified. |
| 2 | Pull authentication history for the relevant time window. | Timeline of failed and successful events. |
| 3 | Compare source IP, device, and location against normal user behavior. | Normal, unusual, or clearly suspicious classification. |
| 4 | Check whether MFA was challenged, denied, approved, or bypassed. | MFA context documented. |
| 5 | Review activity after any successful login. | Evidence of impact or no observed impact. |
| 6 | Search for the same source IP across other accounts. | Scope of attack attempt identified. |
| 7 | Check threat intelligence or reputation sources for the IP/domain if appropriate. | Additional context, not a standalone conclusion. |
| 8 | Decide severity, containment, and escalation. | Recommendation ready for ticket or incident report. |

## Severity Guidance

| Severity | Conditions |
|---|---|
| Low | Failed attempts only, no successful login, source blocked, no privileged account, and no additional indicators. |
| Medium | Repeated failures, unusual source, targeted user, or successful login with no suspicious post-login behavior. |
| High | Successful login from suspicious source, privileged account involved, MFA bypass or fatigue indicators, or suspicious post-login activity. |
| Critical | Confirmed unauthorized access, lateral movement, data access, malware execution, or multiple compromised accounts. |

## Containment Options

Containment should follow organizational policy. Common actions include forcing password reset, revoking active sessions, disabling account temporarily, blocking source IP, requiring MFA re-enrollment, isolating endpoint, and escalating to incident response.

## Documentation Checklist

| Item | Completed |
|---|---|
| Affected account identified |  |
| Timeline created |  |
| Source IP/device/location documented |  |
| MFA result reviewed |  |
| Successful login confirmed or ruled out |  |
| Post-login activity reviewed |  |
| Scope checked across other users |  |
| Severity assigned |  |
| Containment recommendation documented |  |
| Escalation decision documented |  |

## Analyst Notes

This playbook connects strongly to blue-team fundamentals because it requires log analysis, evidence handling, pattern recognition, and clear communication. The goal is not to panic over every unusual login. The goal is to prove what happened, determine impact, and recommend the right response.
