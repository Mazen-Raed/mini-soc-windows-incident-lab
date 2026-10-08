# Mini SOC & Windows Incident Investigation Lab

## Overview

This project is a hands-on Security Operations Center (SOC) lab focused on Windows security monitoring, alert detection, triage, and incident investigation.

The lab simulates a small monitoring environment consisting of a Windows 11 endpoint and a Wazuh-based security monitoring server. Security events are generated on the endpoint, collected and analyzed, then investigated through a structured incident response workflow.

## Objectives

- Monitor Windows security events.
- Detect suspicious activity through security alerts.
- Perform alert triage and investigation.
- Analyze authentication, PowerShell, account, privilege, and process-related activity.
- Create and test custom detection rules.
- Map relevant activity to MITRE ATT&CK.
- Collect and document investigation evidence.
- Build incident timelines and determine appropriate response actions.

## Lab Architecture

```
┌──────────────────────┐
│    Windows 11 VM     │
│      Endpoint        │
└──────────┬───────────┘
           │
      Wazuh Agent
           │
           ▼
┌──────────────────────┐
│    Ubuntu Server     │
│    Wazuh Manager     │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Security Alerts      │
│ & Event Analysis     │
└──────────┬───────────┘
           │
           ▼
┌───────────────────────┐
│ Alert Triage &        │
│ Incident Investigation│
└───────────────────────┘
```

## Environment

| Component | Technology |
|---|---|
| Endpoint | Windows 11 Pro |
| Monitoring Server | Ubuntu Server |
| SIEM / Security Monitoring | Wazuh |
| Virtualization | VirtualBox |
| Security Events | Windows Security Event Logs |
| Investigation Framework | MITRE ATT&CK |

## Investigation Scenarios

### 1. Authentication & Brute-Force Activity

Simulate repeated failed authentication attempts and investigate the resulting Windows security events and Wazuh alerts.

Focus areas:

- Failed authentication attempts
- Source and target account
- Event timestamps
- Authentication-related Windows Event IDs
- Alert severity
- Potential brute-force behavior

### 2. Suspicious PowerShell Activity

Generate selected PowerShell activity and investigate the associated Windows events.

Focus areas:

- PowerShell execution
- Command-line information
- Parent/child process context where available
- Detection logic
- MITRE ATT&CK mapping

### 3. Account Creation

Create a new local Windows account and investigate the associated security events.

Focus areas:

- Account creation events
- Account name
- Event timestamp
- Creating user/context
- Potential security implications

### 4. Privilege & Group Modification

Simulate modification of local group membership and investigate potential privilege escalation activity.

Focus areas:

- Group membership changes
- Privileged group activity
- Affected account
- Security event correlation
- MITRE ATT&CK mapping

### 5. Suspicious Process Activity

Investigate selected process execution activity and identify potentially suspicious behavior.

Focus areas:

- Process execution
- Process names
- Command-line information
- Parent/child process relationships
- Event correlation

## Detection Engineering

The project includes custom Wazuh detection rules for selected Windows security activities.

Detection development includes:

- Rule creation
- Rule testing
- Alert validation
- Severity classification
- False-positive consideration
- MITRE ATT&CK mapping

## Alert Investigation Workflow

Each selected security alert follows a structured investigation process:

1. Alert identification
2. Initial triage
3. Event analysis
4. User and host identification
5. Timeline reconstruction
6. Evidence collection
7. Activity correlation
8. MITRE ATT&CK mapping
9. Severity assessment
10. Response recommendation

## Investigation Documentation

Each completed investigation will document:

- Incident summary
- Detection source
- Affected host
- User/account
- Relevant timestamps
- Observed activity
- Supporting evidence
- Investigation timeline
- MITRE ATT&CK technique
- Severity
- Recommended response

## Project Structure

```
mini-soc-windows-incident-lab/
│
├── README.md
│
├── architecture/
│   └── lab-architecture.png
│
├── detections/
│   ├── custom-rules/
│   └── rule-testing/
│
├── investigations/
│   ├── authentication/
│   ├── powershell/
│   ├── account-creation/
│   ├── privilege-modification/
│   └── process-activity/
│
├── evidence/
│   └── screenshots/
│
└── reports/
    └── incident-reports/
```

## Current Status

**Project Status: In Progress**

### Completed

- Windows 11 virtual endpoint configured.
- Ubuntu Server virtual machine deployed.
- Initial lab environment established.
- Lab architecture defined.
- Investigation scenarios defined.

### In Progress

- Wazuh Manager deployment
- Windows endpoint integration
- Security event collection and validation

### Planned

- Custom Wazuh detection rules
- Security event generation
- Alert triage
- Incident investigations
- Evidence collection
- Timeline analysis
- MITRE ATT&CK mapping
- Incident documentation and final findings

## Skills Demonstrated

- Windows Security Monitoring
- Security Event Analysis
- SIEM Fundamentals
- Alert Triage
- Incident Investigation
- Detection Engineering
- Log Analysis
- MITRE ATT&CK
- Technical Documentation

## Disclaimer

This project is conducted in an isolated virtual laboratory environment for defensive cybersecurity training and incident investigation purposes.
