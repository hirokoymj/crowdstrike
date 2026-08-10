# Exam Objectives

## 1. User Management

- 1.1 Determine roles required for access to features and functionality in the Falcon console
- 1.2 Create roles and assign users to roles based on desired permissions

### 1.3 Manage API keys

- Host setup and management > User management> click my email > right panel > View details page
- `Assign roles`, `Assign temporary roles`
- Support and resources > API clients and keys > Create API client > `test-hosts-read-only,Hosts: Read` > Generated Name, Scope and Base URL.
- at least previlage

```
Client ID: xxxxb7b98
Secret: xxxxx2em
https://api.us-2.crowdstrike.com
```

- Name, scope , B

- Step 5 — Understand what you just made
  This Client ID/Secret pair is how a script or SIEM would authenticate to the Falcon API via OAuth2 — completely separate from your user login and MFA. One CID can have multiple API clients, each scoped narrowly for its own integration, so a compromised script credential doesn't expose everything.

## 2. Sensor Deployment

- 2.1 Determine prerequisites to successfully install a Falcon sensor on supported
  operating systems
- 2.2 Analyze the default policies and apply the best practices to prepare workloads for the
  Falcon sensor
- 2.3 Uninstall a sensor
- 2.4 Troubleshoot a sensor

```
ls ~
   sudo dpkg -i ~/falcon-sensor*.deb
sudo /opt/CrowdStrike/falconctl -s --cid=<YOUR_CID>
 sudo systemctl start falcon-sensor
 sudo systemctl status falcon-sensor

sudo /opt/CrowdStrike/falconctl -s --cid=xxxx
sudo apt remove --purge falcon-sensor
sudo systemctl status falcon-sensor
sudo /opt/CrowdStrike/falconctl -g --cid
ps -e | grep falcon

```

## 3. Host Management and Setup

- 3.1 Understand how filtering might be used in the Host Management page - DONE
- 3.2 Disable detections for a host - DONE

### 3.3 Explain the effect of disabling detections on a host

- detections ≠ prevention.
- Disabling detections does not turn off the sensor's protection.

- 3.4 Explain the impact of Reduced Functionality Mode (RFM) and why it might be caused
- 3.5 Find hosts in RFM
- 3.6 Locate inactive sensors
- 3.7 Recall how long inactive sensors are retained
- 3.8 Determine relevant reports specific to host management

## 4. Group Creation

- 4.1 Determine the appropriate group assignment for endpoints and understand how this impacts
  the application of policies
- 4.2 Apply best practices when managing host groups

## 5. Policy Application

- 5.1 Determine the appropriate prevention policy settings for endpoints and explain how this
  impacts security posture
- 5.2 Determine the appropriate sensor update policy settings in order to control the
  update process
- 5.3 Apply roles and policy settings, and track and review Falcon RTR audit logs in order to
  manage
  user activity
- 5.4 Understand the functionality of a containment policy
- 5.5 Configure a containment policy for IP address or subnet exclusions that will apply to network
  contained hosts based on security workflow requirements
- 5.6 Understand options and requirements to manage quarantined files

## 6. Rules Configuration

- 6.1 Create custom IOA rules to monitor for behavior that is not fundamentally malicious
- 6.2 Interpret business requirements in order to allow trusted activity, resolve false positives and
  fix performance issues
- 6.3 Assess IOC settings required for customized security posturing and to manage
  false positives
- 6.4 Understand configurations for CID wide management within General Settings

## 7. Dashboards and Reports

- 7.1 Understand the different types of sensor reports and their use cases
- 7.2 Understand the different audit logs and their use cases

## 8. Workflows

- 8.1 Configure workflows to respond to defined triggers
