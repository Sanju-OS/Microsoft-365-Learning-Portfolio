# Microsoft 365 Common Support Scenarios

## 1. Overview

Microsoft 365 support involves troubleshooting issues across identity, authentication, email, collaboration, storage, devices, applications, licensing, and security.

A Technical Support Engineer should not troubleshoot randomly.

A structured approach is:

```text
User Reports Issue
       ↓
Identify Scope
       ↓
Identify Affected User / Service
       ↓
Check Authentication
       ↓
Check License
       ↓
Check Permissions
       ↓
Check Policies
       ↓
Check Device / Client
       ↓
Check Microsoft 365 Service Health
       ↓
Troubleshoot
       ↓
Validate Resolution
       ↓
Document Root Cause
````

---

# 2. General Microsoft 365 Troubleshooting Method

For almost any Microsoft 365 incident, follow these steps.

## Step 1 — Understand the Problem

Ask:

* What exactly is not working?
* When did the issue start?
* What error message appears?
* Is the issue continuous or intermittent?
* Did anything change recently?

---

## Step 2 — Determine the Scope

Find out whether the issue affects:

```text
One User
     ↓
Multiple Users
     ↓
Department
     ↓
Entire Organization
```

This is extremely important.

If only one user is affected, investigate the user's account, device, configuration, or permissions.

If hundreds of users are affected, investigate the service, tenant configuration, network, or Microsoft 365 outage.

---

## Step 3 — Identify the Service

Determine which service is affected:

* Outlook
* Exchange Online
* Teams
* OneDrive
* SharePoint
* Microsoft Entra ID
* Intune
* Microsoft 365 Apps
* Microsoft Defender
* Microsoft 365 admin services

---

## Step 4 — Check Dependencies

Microsoft 365 services are interconnected.

Example:

```text
Teams
 │
 ├── Entra ID → Identity
 ├── Exchange → Calendar / Mail
 ├── SharePoint → Files
 └── OneDrive → User Files
```

Therefore, a Teams issue may actually be caused by identity, Exchange, SharePoint, licensing, or Conditional Access.

---

# 3. Scenario — User Cannot Sign In

### User reports:

> "I cannot sign in to Microsoft 365."

### Troubleshooting

```text
User
 ↓
Confirm Username / UPN
 ↓
Check Account Status
 ↓
Check Password
 ↓
Check MFA
 ↓
Check Conditional Access
 ↓
Check Sign-in Logs
 ↓
Check Service Health
 ↓
Test Sign-in
```

### Possible causes

* Incorrect username
* Incorrect password
* Account disabled
* MFA problem
* Conditional Access block
* Authentication issue
* Service outage
* Browser/session issue

### Resolution

Identify the actual authentication failure and apply the appropriate remediation.

---

# 4. Scenario — Password Reset

### User reports:

> "I forgot my Microsoft 365 password."

### Troubleshooting

```text
Verify User
 ↓
Check Account Status
 ↓
Determine Reset Method
 ↓
Reset Password
 ↓
User Signs In
 ↓
Validate Access
```

Depending on the organization's configuration, password reset may be performed by an administrator or through self-service password reset.

### Important

Never request or record a user's password.

---

# 5. Scenario — MFA Not Working

### User reports:

> "I cannot complete MFA."

### Investigation

```text
User
 ↓
Authentication Attempt
 ↓
MFA Challenge
 ↓
Check Registered Methods
 ↓
Check Authentication Logs
 ↓
Check Conditional Access
 ↓
Check Device / Authenticator
 ↓
Resolve
```

Possible causes:

* Lost phone
* Incorrect authentication method
* Authenticator problem
* Device issue
* Authentication policy
* Conditional Access
* Temporary service issue

---

# 6. Scenario — Outlook Keeps Asking for Credentials

### User reports:

> "Outlook keeps asking for my password."

### Investigation

```text
Outlook
 ↓
Check Internet
 ↓
Check Account Authentication
 ↓
Check Credential State
 ↓
Check Modern Authentication
 ↓
Check MFA / Conditional Access
 ↓
Check Outlook Profile
 ↓
Check Autodiscover
 ↓
Test
```

Possible causes:

* Authentication problem
* Cached credentials
* Corrupted Outlook profile
* Conditional Access
* MFA issue
* Network problem
* Autodiscover problem

Do not immediately recreate the Outlook profile without understanding the cause.

---

# 7. Scenario — Outlook Will Not Open

### Investigation

```text
Check Error
 ↓
Check Office Applications
 ↓
Check Outlook Process
 ↓
Start Outlook in Safe Mode
 ↓
Check Add-ins
 ↓
Check Profile
 ↓
Check Updates
 ↓
Check Windows Profile
 ↓
Repair / Recreate Profile if Required
```

Possible causes:

* Corrupted profile
* Faulty add-in
* Office installation issue
* Windows profile issue
* Damaged application components

---

# 8. Scenario — Outlook Profile Corruption

### User reports:

> "Outlook was working previously but now it will not connect."

### Investigation

```text
Check Account
 ↓
Check Connectivity
 ↓
Check Authentication
 ↓
Check Autodiscover
 ↓
Test Existing Profile
 ↓
Create New Profile
 ↓
Test
```

A new Outlook profile can be used as a troubleshooting step when the existing profile is suspected to be corrupted.

---

# 9. Scenario — New User Cannot Access Email

### User reports:

> "I am a new employee and Outlook isn't working."

### Investigation

```text
User Created
 ↓
Account Enabled
 ↓
License Assigned
 ↓
Exchange Online Service Plan
 ↓
Mailbox Provisioning
 ↓
Authentication
 ↓
Autodiscover
 ↓
Outlook
```

Possible causes:

* License missing
* Exchange service plan unavailable
* Mailbox not provisioned
* Authentication issue
* Outlook configuration issue

---

# 10. Scenario — User Cannot Send Email

### User reports:

> "I can receive email but cannot send."

### Investigation

```text
Outlook
 ↓
Account Authentication
 ↓
Mailbox
 ↓
Send Operation
 ↓
Exchange Online
 ↓
Mail Flow
 ↓
Transport Rules
 ↓
Recipient
```

Check:

* Error message
* Mailbox status
* Mail flow
* Transport rules
* Recipient address
* Message trace
* Quarantine/security filtering where applicable

---

# 11. Scenario — User Cannot Receive External Email

### User reports:

> "People outside the company cannot email me."

### Investigation

```text
External Sender
 ↓
Recipient Domain
 ↓
DNS
 ↓
MX
 ↓
Exchange Online
 ↓
Mail Flow
 ↓
Security Filtering
 ↓
Mailbox
```

Check:

* MX records
* Exchange Online
* Message trace
* Mail flow rules
* Anti-spam filtering
* Quarantine
* Recipient mailbox

---

# 12. Scenario — Email Going to Junk

### User reports:

> "Important emails are going to Junk."

### Investigation

```text
Sender
 ↓
SPF
 ↓
DKIM
 ↓
DMARC
 ↓
Sender Reputation
 ↓
Microsoft Defender / Exchange Filtering
 ↓
Mailbox
```

Check:

* Message headers
* Sender reputation
* Authentication results
* Anti-spam policies
* Mail flow rules
* User block/safe lists

Do not simply add every sender to a safe list without understanding the reason for the filtering.

---

# 13. Scenario — Email Missing

### User reports:

> "I received an email but now I can't find it."

### Investigation

```text
Search Mailbox
 ↓
Check Deleted Items
 ↓
Check Junk
 ↓
Check Archive
 ↓
Check Rules
 ↓
Check Focused / Other
 ↓
Check Retention / Recovery Options
 ↓
Check Message Trace if appropriate
```

Determine whether the message was:

* Deleted
* Moved
* Archived
* Filtered
* Quarantined
* Never delivered

---

# 14. Scenario — Shared Mailbox Not Appearing

### User reports:

> "The shared mailbox doesn't appear in Outlook."

### Investigation

```text
User
 ↓
Shared Mailbox Exists?
 ↓
User Has Permission?
 ↓
Permission Applied?
 ↓
Outlook Refresh
 ↓
Autodiscover / Profile
 ↓
Test Access
```

Check:

* Shared mailbox existence
* User permissions
* Full Access
* Send As / Send on Behalf where required
* Outlook configuration

---

# 15. Scenario — Distribution Group Not Receiving Email

### User reports:

> "The distribution group isn't receiving messages."

### Investigation

```text
Sender
 ↓
Distribution Group
 ↓
Group Configuration
 ↓
Membership
 ↓
Delivery Management
 ↓
Mail Flow
 ↓
Message Trace
```

Check:

* Group address
* Group membership
* Delivery restrictions
* External sender settings
* Mail flow
* Message trace

---

# 16. Scenario — Teams Cannot Sign In

### User reports:

> "Teams won't let me sign in."

### Investigation

```text
Teams
 ↓
Internet
 ↓
Microsoft Account
 ↓
Entra Authentication
 ↓
MFA
 ↓
Conditional Access
 ↓
License
 ↓
Teams Service Health
 ↓
Client
```

Possible causes:

* Authentication issue
* MFA issue
* Conditional Access
* License problem
* Teams client issue
* Service outage

---

# 17. Scenario — Teams Calls Not Working

### User reports:

> "Teams chat works, but calls don't."

### Investigation

```text
Teams Login
 ↓
License
 ↓
Calling Policy
 ↓
Microphone
 ↓
Camera
 ↓
Speaker
 ↓
Network
 ↓
Firewall / Proxy
 ↓
Teams Service
```

Check both application configuration and endpoint/network conditions.

---

# 18. Scenario — Teams Microphone Not Working

### Investigation

```text
Teams
 ↓
Settings
 ↓
Microphone Selection
 ↓
Windows/macOS Permissions
 ↓
Device Driver
 ↓
Physical Device
 ↓
Test Call
```

Possible causes:

* Wrong microphone selected
* OS permission denied
* Driver issue
* Hardware problem
* Another application using the microphone

---

# 19. Scenario — Teams Camera Not Working

### Investigation

```text
Teams
 ↓
Camera Selection
 ↓
OS Camera Permission
 ↓
Camera Driver
 ↓
Privacy Settings
 ↓
Physical Camera
 ↓
Test
```

Check whether another application is using the camera.

---

# 20. Scenario — Teams Meeting Cannot Be Joined

### Investigation

```text
Meeting Link
 ↓
User Authentication
 ↓
Meeting Permissions
 ↓
Teams Client / Browser
 ↓
Network
 ↓
Meeting Service
```

Try:

* Teams desktop client
* Teams web client
* Another network
* Checking meeting permissions
* Checking service health

---

# 21. Scenario — OneDrive Not Syncing

### User reports:

> "My files are not syncing."

### Investigation

```text
OneDrive
 ↓
Internet
 ↓
Account
 ↓
Storage
 ↓
Sync Status
 ↓
File / Folder Restrictions
 ↓
OneDrive Client
 ↓
Authentication
 ↓
Reset / Reconfigure if Required
```

Possible causes:

* Account authentication
* Network issue
* Storage limit
* File naming/path restrictions
* Sync client issue
* Permission problem

---

# 22. Scenario — OneDrive Red Cloud / Sync Error

### Investigation

```text
Check OneDrive Icon
 ↓
Check Error Message
 ↓
Check Account
 ↓
Check File
 ↓
Check Path
 ↓
Check Storage
 ↓
Check Client
```

Do not immediately delete the local OneDrive folder.

First determine whether the files are synchronized and whether data is safely available elsewhere.

---

# 23. Scenario — SharePoint Access Denied

### User reports:

> "I can access Microsoft 365 but SharePoint says Access Denied."

### Investigation

```text
Authentication
 ↓
License
 ↓
Site Membership
 ↓
Group Membership
 ↓
SharePoint Permissions
 ↓
Sharing Configuration
 ↓
Conditional Access
```

Remember:

```text
Successful Microsoft 365 Login
        ≠
Access to Every SharePoint Site
```

---

# 24. Scenario — SharePoint File Cannot Be Opened

### Investigation

```text
File
 ↓
Site Access
 ↓
Library Permissions
 ↓
File Permissions
 ↓
File Status
 ↓
Version / Lock
 ↓
Application
```

Check whether the user has access to the site, library, and specific file.

---

# 25. Scenario — Microsoft 365 App Activation Failure

### User reports:

> "Word says I need to activate Microsoft 365."

### Investigation

```text
User
 ↓
Account
 ↓
License
 ↓
Subscription
 ↓
Office Sign-In
 ↓
Activation Status
 ↓
Network
 ↓
Office Installation
```

Possible causes:

* No appropriate license
* Wrong account signed in
* Subscription issue
* Activation problem
* Cached identity
* Office installation issue

---

# 26. Scenario — User Has No Microsoft 365 License

### Investigation

```text
User
 ↓
Account Status
 ↓
License Assignment
 ↓
Group Membership
 ↓
Subscription Availability
 ↓
Assignment Error
```

Possible causes:

* License never assigned
* User removed from licensing group
* No available license
* License assignment failed
* Provisioning issue

---

# 27. Scenario — User Can Sign In but Application Access Is Denied

### Investigation

```text
Authentication
       ↓
Successful
       ↓
Authorization
       ↓
Group Membership
       ↓
Application Assignment
       ↓
Conditional Access
       ↓
Device Compliance
```

This is a classic example of:

```text
Authentication ≠ Authorization
```

---

# 28. Scenario — Conditional Access Block

### User reports:

> "I can sign in from my office but not from home."

### Investigation

```text
User
 ↓
Sign-In Attempt
 ↓
Location
 ↓
Device
 ↓
Application
 ↓
Conditional Access
 ↓
MFA
 ↓
Compliance
```

Possible causes:

* Location-based policy
* Device compliance
* MFA requirement
* Risk-based policy
* Application restriction

Conditional Access should be investigated through the appropriate Microsoft Entra sign-in information and policy evaluation.

---

# 29. Scenario — Device Not Compliant

### User reports:

> "I cannot access Microsoft 365 from my laptop."

### Investigation

```text
Device
 ↓
Entra Registration
 ↓
Intune Enrollment
 ↓
Compliance Status
 ↓
Compliance Policy
 ↓
Conditional Access
 ↓
Application Access
```

Possible causes:

* Device not enrolled
* Compliance policy failure
* Encryption requirement
* Security requirement
* OS version requirement
* Conditional Access blocking access

---

# 30. Scenario — New Device Cannot Access Microsoft 365

### Investigation

```text
New Device
 ↓
Internet
 ↓
Entra Registration
 ↓
Intune Enrollment
 ↓
Compliance
 ↓
User Authentication
 ↓
MFA
 ↓
Conditional Access
 ↓
Application
```

This is a good example of how identity and endpoint management interact.

---

# 31. Scenario — Microsoft 365 Service Outage

### Problem

Multiple employees report:

> "Outlook and Teams are not working."

### First question

Is this:

```text
One User
```

or:

```text
Multiple Users?
```

If multiple users are affected:

```text
Check Microsoft 365 Service Health
        ↓
Identify Incident
        ↓
Confirm Scope
        ↓
Follow Microsoft Updates
        ↓
Communicate to Users
        ↓
Validate Recovery
```

Avoid changing user configurations unnecessarily during a confirmed service incident.

---

# 32. Scenario — Only One User Is Affected

If the organization confirms the service is working for everyone else:

```text
Service Healthy
      ↓
Single User Affected
      ↓
User Account
      ↓
License
      ↓
Permissions
      ↓
Device
      ↓
Application
      ↓
User Configuration
```

This helps narrow the scope.

---

# 33. Scenario — Multiple Users Are Affected

If multiple users are affected:

```text
Multiple Users
      ↓
Common Service?
      ↓
Service Health
      ↓
Tenant Configuration
      ↓
Network
      ↓
Policy
      ↓
Recent Changes
```

Look for common dependencies.

---

# 34. Scenario — Password Works but Sign-In Fails

A valid password does not guarantee successful access.

Investigation:

```text
Password
   ↓
Authentication
   ↓
MFA
   ↓
Conditional Access
   ↓
Device Compliance
   ↓
Application Access
```

Possible causes:

* MFA failure
* Conditional Access
* Device compliance
* Authentication policy
* Risk-based restrictions

---

# 35. Scenario — User Is Locked Out

### Investigation

```text
User
 ↓
Account Status
 ↓
Sign-In Attempts
 ↓
Authentication Methods
 ↓
MFA
 ↓
Conditional Access
 ↓
Possible Compromise
```

If suspicious activity is suspected, follow the organization's security incident process rather than treating the issue as a simple password problem.

---

# 36. Scenario — Guest User Cannot Access Resource

### Investigation

```text
Guest User
 ↓
Invitation
 ↓
Guest Account
 ↓
Authentication
 ↓
External Collaboration Settings
 ↓
Resource Permissions
 ↓
Conditional Access
 ↓
Resource
```

Check both the guest identity and the resource's sharing configuration.

---

# 37. Scenario — User Cannot Access Teams Channel

### Investigation

```text
User
 ↓
Teams Membership
 ↓
Channel Type
 ↓
Channel Membership
 ↓
Permissions
 ↓
Policy
 ↓
Application
```

Pay attention to whether the channel is:

* Standard
* Private
* Shared

Different channel types can have different membership and access behavior.

---

# 38. Scenario — Outlook Calendar Not Updating

### Investigation

```text
Outlook
 ↓
Internet
 ↓
Authentication
 ↓
Exchange Online
 ↓
Mailbox
 ↓
Calendar
 ↓
Outlook Client
 ↓
Profile
```

Determine whether the problem affects:

* One calendar
* One user
* Multiple users
* All users

---

# 39. Scenario — Shared Calendar Access Problem

### Investigation

```text
User
 ↓
Calendar
 ↓
Permission
 ↓
Mailbox / Resource
 ↓
Exchange Online
 ↓
Outlook
```

Verify that the user has the appropriate calendar permissions.

---

# 40. Scenario — User Cannot Install Microsoft 365 Apps

### Investigation

```text
User
 ↓
License
 ↓
Application Entitlement
 ↓
Admin Restrictions
 ↓
Device
 ↓
Operating System
 ↓
Network
 ↓
Installation
```

Possible causes:

* License does not include desktop applications
* Administrative restrictions
* Unsupported device
* Installation issue
* Network issue

---

# 41. Scenario — Microsoft 365 Application Crashes

Examples:

* Word crashes
* Excel crashes
* Outlook crashes
* Teams crashes

### Investigation

```text
Application
 ↓
Error Message
 ↓
Updates
 ↓
Add-ins
 ↓
Cache / Profile
 ↓
OS
 ↓
Device
 ↓
Repair / Reinstall if Required
```

Use the least disruptive remediation first.

---

# 42. Scenario — Microsoft 365 App Is Slow

### Investigation

```text
Application
 ↓
Internet
 ↓
Network Latency
 ↓
Service Health
 ↓
Device Resources
 ↓
Application Version
 ↓
User Profile
 ↓
Background Processes
```

Determine whether the slowness is:

```text
Application
     OR
Device
     OR
Network
     OR
Microsoft Service
```

---

# 43. Scenario — User Reports "Everything Is Slow"

Do not immediately blame Microsoft 365.

Check:

```text
Device
 ↓
CPU
 ↓
Memory
 ↓
Disk
 ↓
Network
 ↓
Internet
 ↓
Microsoft 365 Service
 ↓
Application
```

This is an example of proper technical troubleshooting.

---

# 44. Scenario — Email Authentication Failure

### Problem

> "External recipients say our emails are failing authentication."

Investigate:

```text
Domain
 ↓
SPF
 ↓
DKIM
 ↓
DMARC
 ↓
DNS
 ↓
Sending Source
 ↓
Message Headers
```

Verify that legitimate sending systems are correctly represented in the organization's email authentication configuration.

---

# 45. Scenario — Mail Flow Problem

### Investigation

```text
Sender
 ↓
Exchange Online
 ↓
Transport
 ↓
Mail Flow Rules
 ↓
Security Filtering
 ↓
Recipient
 ↓
Message Trace
```

Message Trace is an important tool for investigating Exchange Online mail-flow issues.

---

# 46. Scenario — User Deleted an Email

### Investigation

```text
Mailbox
 ↓
Deleted Items
 ↓
Recoverable Items / Recovery Options
 ↓
Retention / Organizational Policy
 ↓
Recovery
```

Do not assume a permanently deleted email can always be recovered.

Recovery depends on the mailbox configuration, retention settings, deletion state, and organizational policies.

---

# 47. Scenario — OneDrive File Accidentally Deleted

### Investigation

```text
OneDrive
 ↓
Recycle Bin
 ↓
Second-Stage Recycle Bin where applicable
 ↓
Version / Recovery Options
 ↓
Retention Policies
```

Follow the organization's data recovery procedures.

---

# 48. Scenario — User Cannot Access OneDrive After Account Change

### Investigation

```text
User
 ↓
Account
 ↓
License
 ↓
OneDrive
 ↓
SharePoint
 ↓
Permissions
 ↓
Authentication
 ↓
Device
```

A user account change can affect access to Microsoft 365 resources.

---

# 49. Scenario — Mobile Device Cannot Access Microsoft 365

### Investigation

```text
Mobile Device
 ↓
Internet
 ↓
User Authentication
 ↓
MFA
 ↓
Intune Enrollment
 ↓
Compliance
 ↓
Conditional Access
 ↓
Application
```

Check whether the organization requires device enrollment or compliance before access.

---

# 50. Scenario — Browser Works but Desktop App Does Not

### Problem

```text
Browser → Works
Desktop App → Fails
```

This is useful diagnostic information.

Investigate:

```text
Desktop Application
 ↓
Cache
 ↓
Credentials
 ↓
Profile
 ↓
Application Version
 ↓
Add-ins
 ↓
Device
```

If the browser works, the Microsoft 365 service itself may not be the primary problem.

---

# 51. Scenario — Desktop App Works but Browser Does Not

Investigate:

```text
Browser
 ↓
Cookies
 ↓
Cache
 ↓
Extensions
 ↓
Authentication Session
 ↓
Browser Version
 ↓
Network
```

Testing another supported browser can help isolate the problem.

---

# 52. Scenario — User Reports Intermittent Problems

### Problem

> "Sometimes Outlook works and sometimes it doesn't."

Do not treat this as a simple configuration issue.

Investigate:

```text
Time of Failure
 ↓
Network
 ↓
Connectivity
 ↓
Authentication
 ↓
Service Health
 ↓
Device
 ↓
Application Logs
 ↓
Pattern
```

Look for a reproducible pattern.

---

# 53. Scenario — Recent Configuration Change

If an issue started immediately after a change:

```text
Issue Started
      ↓
Recent Change?
      ↓
Identify Change
      ↓
Determine Impact
      ↓
Rollback / Remediate
      ↓
Validate
```

Examples:

* Conditional Access policy changed
* License changed
* DNS changed
* Mail flow rule changed
* Group membership changed
* Teams policy changed

A timeline is often a powerful troubleshooting clue.

---

# 54. Incident Prioritization

Not every Microsoft 365 issue has the same priority.

Consider:

```text
Number of Users
      +
Business Impact
      +
Security Impact
      +
Service Criticality
      =
Priority
```

Example:

```text
One user cannot access Teams
        ↓
Potentially lower priority

Entire organization cannot send email
        ↓
High business impact

Suspicious account compromise
        ↓
High security priority
```

Actual priority should follow the organization's ITSM process.

---

# 55. Troubleshooting vs Guessing

Bad approach:

```text
Problem
 ↓
Restart
 ↓
Reinstall
 ↓
Reset Everything
```

Better approach:

```text
Problem
 ↓
Gather Evidence
 ↓
Identify Scope
 ↓
Form Hypothesis
 ↓
Test
 ↓
Identify Root Cause
 ↓
Remediate
 ↓
Validate
 ↓
Document
```

---

# 56. Root Cause Analysis

A good support engineer should distinguish:

### Symptom

What the user sees.

Example:

```text
"Outlook won't connect."
```

### Cause

What actually created the problem.

Example:

```text
Conditional Access policy blocked authentication.
```

### Resolution

What fixed the problem.

Example:

```text
Corrected the policy assignment after validating the intended access requirements.
```

---

# 57. Incident Documentation Template

Use this structure when documenting support incidents:

```text
Incident Title:
____________________________

Affected Service:
____________________________

Affected User(s):
____________________________

Business Impact:
____________________________

Reported Issue:
____________________________

Error Message:
____________________________

Scope:
____________________________

Initial Checks:
____________________________

Troubleshooting Performed:
____________________________

Root Cause:
____________________________

Resolution:
____________________________

Validation:
____________________________

Preventive Action:
____________________________
```

---

# 58. Example Incident Documentation

## Incident

```text
Title:
User unable to access Microsoft Teams
```

### Affected Service

```text
Microsoft Teams
```

### Reported Issue

```text
User cannot sign in to Teams.
```

### Investigation

```text
Account checked
 ↓
License checked
 ↓
MFA checked
 ↓
Conditional Access checked
 ↓
Sign-in information reviewed
```

### Root Cause

```text
Authentication policy prevented the expected sign-in flow.
```

### Resolution

```text
Corrected the applicable configuration according to organizational policy.
```

### Validation

```text
User successfully signed in and verified Teams functionality.
```

---

# 59. Universal Microsoft 365 Troubleshooting Framework

Use this framework across Microsoft 365:

```text
                INCIDENT
                    │
                    ▼
              DEFINE ISSUE
                    │
                    ▼
               IDENTIFY SCOPE
                    │
          ┌─────────┴─────────┐
          │                   │
       ONE USER          MANY USERS
          │                   │
          ▼                   ▼
       USER SIDE          SERVICE SIDE
          │                   │
          └─────────┬─────────┘
                    ▼
               IDENTIFY SERVICE
                    │
                    ▼
              CHECK IDENTITY
                    │
                    ▼
             CHECK LICENSE
                    │
                    ▼
            CHECK PERMISSIONS
                    │
                    ▼
             CHECK POLICIES
                    │
                    ▼
          CHECK DEVICE / CLIENT
                    │
                    ▼
             CHECK NETWORK
                    │
                    ▼
            CHECK SERVICE HEALTH
                    │
                    ▼
             TEST HYPOTHESIS
                    │
                    ▼
                REMEDIATE
                    │
                    ▼
                VALIDATE
                    │
                    ▼
              DOCUMENT ROOT CAUSE
```

---

# 60. Key Support Principles

A Microsoft 365 Technical Support Engineer should:

1. Understand the reported issue.
2. Identify the affected service.
3. Determine the scope.
4. Check whether the issue affects one or multiple users.
5. Check identity and authentication.
6. Check licensing.
7. Check permissions.
8. Check security policies.
9. Check the device and client.
10. Check network connectivity.
11. Check Microsoft 365 service health.
12. Gather evidence.
13. Avoid unnecessary changes.
14. Apply the least disruptive remediation.
15. Validate the solution.
16. Document the root cause.
17. Communicate clearly with the user.
18. Escalate when the issue exceeds the support boundary.

---

# 61. Portfolio Learning Outcome

After completing this topic, I should be able to:

* Troubleshoot common Microsoft 365 incidents.
* Identify affected services.
* Determine incident scope.
* Troubleshoot user authentication.
* Troubleshoot licensing problems.
* Troubleshoot Outlook issues.
* Troubleshoot Exchange Online mail flow.
* Troubleshoot Teams.
* Troubleshoot OneDrive.
* Troubleshoot SharePoint.
* Troubleshoot Microsoft 365 application issues.
* Understand Intune-related access issues.
* Understand Conditional Access scenarios.
* Use a structured L1/L2 troubleshooting methodology.
* Perform basic root cause analysis.
* Document incidents professionally.
* Validate resolutions.
* Escalate issues appropriately.
