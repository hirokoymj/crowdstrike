# CrowdStrike Falcon Admin

_9:15 AM, 7/31/2026_

## What is CrowdStrike / EDR

Endpoint Detection and Response (EDR), also referred to as endpoint detection and threat response (EDTR), is an endpoint security solution that continuously monitors end-user devices to detect and respond to cyber threats like ransomware and malware.

## Demo: Overview of the Console

**Endpoint security > Activity dashboard**

- Current CrowdScore: 0/100
- New detections: 7
- SHA-based detections
- Prevented malware by host: None
- Total OverWatch-analyzed events
- OverWatch endpoint hunting leads
- OverWatch endpoint detections triggered
- CrowdScore over time
- Most recent detections – 1 Critical and 2 High

**Pages**

- CrowdScore incidents
- Endpoint security > detections

**Left menu**

- Next-Gen SIEM
- Endpoint security
- Investigate >
- Fusion SOAR = Automated workflow
- Dashboards and reports >
- Host setup and management > Host management
- Host setup and management > Host dashboard
- Support and resources > Documentation

## Users and Roles

- Falcon admin – Me
- User – must have an associated domain

**Top Roles:**

- Falcon Admin
- Prevention Policy Admin
- Falcon console guest
- Dashboard Admin
- Desktop Support Analyst
- Workflow Author
- Help Desk Analyst

**How to add a new user:**
Host setup > Falcon users > User management

### Demo: Users and Roles

**User profile** — Host setup and management > User management

- User email
- User name
- Roles
- Temp roles
- Created at
- Last login
- Create User btn

**User detail page**

- User info
- Roles (26)
- Assign roles
- Edit user info

**Documentation:** Falcon Documentation: falcon-us-2.crowdstrike.com/documentation

**Real Time Responder (RTR) roles**

**General settings**

- Notifications > Detection and incident emails

## Installation

**Manual install (1-1)**

- Host setup and management > Sensor downloads > installer based on OS > download > copy CID
- pkg file

**Automatic install (1-many)**

- Host setup and management > Sensor downloads > installer based on OS > download > copy CID
- Run on CLI

**Points**

- Make sure OS matches
- Sensor Release Matrix (N-1, N-2)
- Network dependency: outbound SSL traffic (443)
- Windows Installer
- Linux Install
- Installation Tokens > Add token
- provisioning-token `<token>`, MAX 50 tokens per CID

### Demo: Installing Sensors

- Installing tokens -> Add Token (BTC install Token, 30 day)
- See audit log
- Require tokens checked

**Sensor Downloads > Download Latest Sensor — How to Install**

1. Download the latest sensor installer for your platform.
2. Copy your Customer ID checksum to enter during install: `DA41AA34774B49BFB4BA5E88F0F91529-C2`
3. Run the installer on the endpoint. For installing via systems management tool or reusable VM images, see the Deployment Guides.

- Download List -> Download -> CrowdStrike Falcon Sensor Setup dialog

**Install command example (PowerShell):**

```
PS C:\Users\hailie\Desktop> .\WindowsSensor.MaverickGyr.exe /install /quiet /norestart
CID=DA41AA34774B49BFB4BA5E88F0F91529-C2 MAINTENANCE_TOKEN=D299678E

PS C:\Users\hailie\Desktop> sc.exe query csagent

SERVICE_NAME: csagent
    TYPE               : 2  FILE_SYSTEM_DRIVER
    STATE              : 4  RUNNING
                              (STOPPABLE, NOT_PAUSABLE, IGNORES_SHUTDOWN)
    WIN32_EXIT_CODE    : 0  (0x0)
    SERVICE_EXIT_CODE  : 0  (0x0)
    CHECKPOINT         : 0x0
    WAIT_HINT          : 0x0
```

## Troubleshooting

**Uninstalling & Sensor updates**

1. Control panel > Programs and features > Uninstall
2. Download a CS uninstall tool from Tool Downloads in console
3. Support > Tool download > Sensor removal tool based on OS > download it

**Uninstall via CLI:**

```
csuninstalltool.exe MAINTENANCE_TOKEN=<token> /quiet
CsUninstallTool.exe /quiet
```

- Cannot uninstall without a token if maintenance protection is enabled
- Bulk maintenance mode
- Bulk Uninstall

**Sensor Updating**
Host setup and management > Sensor update policies > Create new > name it > create

## Host Management

### Demo: Sensor Update Policies — BTC-Windows

- Host targeting
- Policy assignment
  - Prevention policies
  - Sensor update policies
- Exclusions

### Demo: Host Groups

**Add New Group > New Group Details**

- NAME: BTC-Windows
- DESCRIPTION: all hosts that are Windows OS
- Group Type:
  - **Dynamic**: create a rule to automatically add/remove hosts based on filters
  - **Static by host ID**: add/remove hosts based on host ID
  - **Static by hostname**: add/remove hosts based on hostname
- Edit > Filter (Platform: Windows) > 2 hosts > Save

**Additional groups:**

- Host Groups > BTC-Windows page
- New Group Details (BTC-MacOS, Dynamic) > Filter (platform: Mac)
- New Group Details (BTC-Linux, Dynamic) > Filter (platform: Linux)

## Prevention Policies

**Prevention Policy**: the set of rules controlling how the Falcon sensor detects and blocks malware/threats on a host — settings like malware prevention, exploit mitigation, and machine learning detection levels, applied to specific host groups. Without one assigned, a host is unprotected.

### Make one:

`endpoint security>prevention policies>create new>platform>name>create`

### Enable:

`settings>save>confirm>enable>enable policy`

### Precedence order

This list represents the precedence order in which CrowdStrike applies prevention policies to a host — Default sits at the lowest precedence (a catch-all for hosts not assigned to a custom policy), while Phase 1–3 are custom policies with higher precedence, assigned to specific host groups as you progress through deployment. "Prevention Policy Precedence" is an accurate title for it.

- Phase 3: Full standard protection
- Phase 2: Interim protection, no AV/EDR in place
- Phase 1: Rapid deployment, minimal protection
- Default (lowest precedence): Out-of-box policy, applies before custom phases are set

AV = antivirus — traditional signature-based malware detection.

EDR = Endpoint Detection and Response — monitors endpoint activity in real time to detect, investigate, and respond to threats (like Falcon itself). AV mainly blocks known malware; EDR watches for suspicious behavior, including attacks AV would miss.

### Demo: Prevention Settings

### Custom IOAs

Demo: Creating Custom IOAs

### Exclusions and Quarantines — Reviewing Exclusions

**Machine Learning exclusions**

Create machine learning exclusion – 1

- Targeted hosts: All hosts
- Excluded from:
  - ☑ Detections and preventions
  - ☑ Uploads to CrowdStrike
- Exclusion pattern: `\ProgramData\McAfee\**`

Create machine learning exclusion – 2

- Exclusion pattern: `\Program Files\wireshark.exe`

### References

- [Udemy CrowdStrike: Zero to Falcon Admin](https://ttsus.udemy.com/course/crowdstrike-zero-to-falcon-admin/learn/lecture/36461842?start=30#overview)
- [Prevention Policy | CrowdStrike Developer Center](https://developer.crowdstrike.com/api-reference/collections/prevention-policy/)
- [CrowdStrike Prevention Policies: Reduce False Positives & Block Ransomware | Inventive HQ](https://inventivehq.com/knowledge-base/crowdstrike/how-to-setup-prevention-policies-in-crowdstrike-falcon)
