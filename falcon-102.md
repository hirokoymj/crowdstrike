# FALCON 102: Falcon Platform Onboarding Configuration

`6 Modules/2 hours`

https://university.crowdstrike.com/learn/courses/472/falcon-102-falcon-platform-onboarding-configuration

## Setting up users and planning implementation

- Never rely on a single administrator account
- At least two Falcon Administrators are recommended.
- Host setup and management > User management
- Real-Time Response role, Custom role, Admin role
- CrowdStrike Only
- Short-term coexisting - OK - An antivirus is removed after verifying Falcon is tuned.
- Long-term coexisting X
- https://docs.crowdstrike.com/r/en-US/iopiipqy/ea9b123c
- Reduced Functionality Mode (RFM) =
- real-time detection updates and event reporting.
- Host setup and management > Sensor health.

## Configuring single sign-on, alert notifications, and prevention policies

- 2FA vs SSO
- CS supports - Active Directory, Okta, PingFederate, Azure AD
- Support and resources > Documentation > Falcon Management > Account Settings > Single-Sign On for Falcon
- Early notification
- high-priority alerts
- three notification types - Email, Fusion Soar, Schedule search notification
- (Email) Support and resources > General settings > Notifications
- e.g. low severity incidents > workflow with Fusion SOAR
- Fusion SOAR > Workflows
- Investigate > Scheduled search > Create scheduled search
- prevention policies
- Enpoint security > Prevention policies > Default policy
- Default policy == assigned all hosts
- Separate policies need for Win/Mac/Linux.
- Endpoint security > Configure > Prevention policies
- Policy precedence
- Phase One prevention policies
- three-phased prevention policy
- sensor update policies
- Configuring Prevention Policies
- Phase 1, 2, 3 / minimal, modelate, full
- Phase One prevention policies - CS + antivirus

## Create sensor update policies and additional configurations

https://university.crowdstrike.com/learn/courses/472/falcon-102-falcon-platform-onboarding-configuration/lessons/7649:1575/create-sensor-update-policies-and-additional-configurations

- Auto (Latest) - Testing groups
- Auto (N-1) - second newest sensor version
- Auto (N-2) - Third newest sensor version
- Updates OFF
- requires a token
- prevents unauthorized sensor removal and controls maintenance actions
- Bulk maintenance mode allows administrators to use a single token to uninstall or upgrade all hosts within a specific policy.

## Managing host groups for endpoint policy enforcement

Done (9/1)

## Managing false positives and exclusions

## Navigating and optimizing Falcon support reso

--

## Sensor visibility exclusions

Endpoint security -> Exclusions > Sensor visibility exclusions >

- to stop collecting any telemetry for files/paths that match the pattern — no event logging, no detections, no preventions for anything under that path.

https://university.crowdstrike.com/learn/courses/472/falcon-102-falcon-platform-onboarding-configuration
