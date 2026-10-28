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


The current lab uses built-in Wazuh detection rules to collect and review selected Windows security events and alerts.

Custom detection engineering is planned for a later phase.

Planned activities include:

* Developing custom Wazuh rules for selected Windows security events.
* Testing rule behavior against controlled lab activity.
* Validating generated alerts.
* Assigning appropriate severity levels.
* Reviewing potential false positives.
* Mapping relevant detections to MITRE ATT&CK where applicable.
  
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


* Configured a Windows 11 Pro virtual endpoint.
* Deployed an Ubuntu Server virtual machine for security monitoring.
* Installed and configured the Wazuh monitoring environment.
* Registered and connected the Windows endpoint to Wazuh using the Wazuh Agent.
* Verified that the endpoint was active and reporting security events.
* Observed and examined Windows security events in the Wazuh Threat Hunting interface.
* Identified and reviewed Windows Event ID 4625 (failed logon).
* Identified and reviewed Windows Event ID 4720 (user account creation).
* Examined Windows Event ID 7045 (service installation).
* Verified PowerShell Script Block Logging events (Event ID 4104) in Windows Event Viewer.
* Captured initial screenshots documenting the lab environment and selected security events.

#### In Progress

* Organizing investigation evidence and screenshots.
* Documenting observed security events and their significance.
* Developing structured investigation notes for selected events.
* Expanding security event analysis and correlation.

#### Planned

* Develop and test custom Wazuh detection rules.
* Investigate authentication failures as a potential brute-force scenario.
* Analyze PowerShell activity and its execution context.
* Investigate account creation and local group membership changes.
* Analyze suspicious process activity and related telemetry.
* Map relevant findings to MITRE ATT&CK.
* Build incident timelines from collected event data.
* Produce structured incident investigation reports with supporting evidence and response recommendations.

#### Current Scope

The lab currently demonstrates Windows endpoint integration, security event collection, and initial event examination using existing Wazuh detection rules.

Custom detection engineering, structured incident investigations, timeline reconstruction, and formal incident reporting remain planned development tasks.

### Evidence & Initial Findings

This section documents the initial evidence collected during the lab setup and Windows security event monitoring activities.

#### 1. Wazuh Endpoint Integration

The Windows 11 endpoint was successfully registered with Wazuh and appeared as an active agent.

The endpoint details confirmed the agent name, IP address, operating system, and connection status.

**Evidence:**

* Wazuh Endpoints Summary.
* Wazuh Agent Details.

#### 2. Failed Logon Event

Windows Event ID 4625 was observed in Wazuh.

This event records a failed logon attempt and provides information that can support authentication-related investigation.

**Evidence:**

* Wazuh Threat Hunting results.
* Event document details showing Event ID 4625 and associated event fields.

#### 3. Service Installation Event

Windows Event ID 7045 was observed in Wazuh.

This event records the installation of a service. Further investigation is required to determine whether a specific service is expected, unusual, or potentially suspicious.

**Evidence:**

* Wazuh event document details showing Event ID 7045 and Service Control Manager information.

#### 4. User Account Creation Event

Windows Event ID 4720 was observed in Wazuh.

This event records the creation of a user account and can support investigations into account management activity.

**Evidence:**

* Wazuh Threat Hunting results.
* Event document details showing Event ID 4720 and the account creation message.

#### 5. PowerShell Script Block Logging

PowerShell Event ID 4104 was observed in the local Windows Event Viewer under the PowerShell Operational log.

The event details included information about the recorded script block, the associated user, the host, and the event timestamp.

**Evidence:**

* Windows PowerShell Operational event log.
* Event Properties showing Event ID 4104 and recorded event details.

### Investigation Notes

The evidence collected so far confirms that the lab can receive and display selected Windows security events through Wazuh and the local Windows Event Viewer.

The presence of an event does not, by itself, establish malicious activity. Additional context, event correlation, and investigation are required before determining whether activity is suspicious.

The documented findings represent initial event examination rather than completed incident investigation reports.



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
