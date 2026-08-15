# Microsoft 365 Services

## 1. Overview

Microsoft 365 is made up of multiple cloud services that work together to provide productivity, communication, collaboration, identity, endpoint management, security, compliance, automation, and AI capabilities.

For a Technical Support or L2 Support Engineer, it is important to understand not only what each service does, but also how the services interact.

A simplified view is:

```text
Microsoft 365
│
├── Productivity
│   ├── Word
│   ├── Excel
│   ├── PowerPoint
│   └── OneNote
│
├── Communication & Collaboration
│   ├── Outlook
│   ├── Exchange Online
│   ├── Microsoft Teams
│   ├── SharePoint Online
│   └── OneDrive
│
├── Identity
│   └── Microsoft Entra ID
│
├── Endpoint Management
│   └── Microsoft Intune
│
├── Security
│   └── Microsoft Defender
│
├── Compliance
│   └── Microsoft Purview
│
├── Automation
│   └── Power Platform
│
└── AI
    └── Microsoft 365 Copilot
```

---

# 2. Core Microsoft 365 Services

## Microsoft Outlook

Outlook is a client application used for:

* Email
* Calendar
* Contacts
* Tasks
* Meeting scheduling

Outlook commonly connects to Exchange Online for organizational email and calendar services.

### Support areas

An IT support engineer may troubleshoot:

* Outlook not opening
* Password prompts
* Profile corruption
* Send/receive problems
* Autodiscover
* Calendar problems
* Search problems
* Shared mailbox access
* Add-in problems
* Performance issues

---

# 3. Exchange Online

Exchange Online is Microsoft's cloud-hosted email and calendaring service.

It provides:

* User mailboxes
* Shared mailboxes
* Resource mailboxes
* Distribution groups
* Mail flow
* Transport rules
* Connectors
* Message trace
* Anti-spam
* Anti-malware
* Quarantine

Simplified architecture:

```text
User
 ↓
Outlook
 ↓
Exchange Online
 ↓
Mailbox
 ↓
Mail Flow
 ↓
Recipient
```

### Support areas

Common incidents include:

* Email not sending
* Email not receiving
* NDRs
* Delayed messages
* Spam/quarantine issues
* Shared mailbox access
* Distribution group problems
* Mail flow problems

---

# 4. Microsoft Teams

Microsoft Teams provides communication and collaboration capabilities.

It supports:

* Chat
* Teams
* Channels
* Meetings
* Calls
* Screen sharing
* File collaboration
* Apps
* Breakout rooms
* Whiteboard
* Meeting recording

Teams integrates with other Microsoft services.

For example:

```text
Teams
 │
 ├── Identity → Entra ID
 │
 ├── Files → SharePoint
 │
 ├── User Files → OneDrive
 │
 └── Meetings / Calendar → Exchange Online
```

### Support areas

Common issues include:

* Teams sign-in failure
* Meeting problems
* Audio problems
* Camera problems
* Screen sharing problems
* Connectivity problems
* Missing teams/channels
* Permission problems
* Teams client issues

---

# 5. SharePoint Online

SharePoint Online is Microsoft's cloud service for content management, collaboration, intranet sites, and document management.

It provides:

* Sites
* Document libraries
* Lists
* Pages
* Permissions
* Sharing
* Version history
* Recycle Bin
* Search

A simplified relationship:

```text
Microsoft Teams
       │
       ▼
    Channels
       │
       ▼
SharePoint Online
       │
       ▼
Document Libraries
```

### Support areas

Common issues include:

* Access denied
* Missing permissions
* Sharing problems
* Document access problems
* Synchronization problems
* External sharing problems
* Site access problems

---

# 6. OneDrive for Business

OneDrive for Business provides cloud-based storage for an individual user's organizational files.

It supports:

* File storage
* Synchronization
* File sharing
* Version history
* Files On-Demand
* Recovery
* Collaboration

Simplified model:

```text
User
 ↓
OneDrive
 ↓
Microsoft Cloud
 ↓
Files
```

### Support areas

Common issues include:

* OneDrive not syncing
* Files missing
* Login problems
* Storage problems
* Sharing issues
* Sync conflicts
* Files On-Demand problems

---

# 7. Microsoft Entra ID

Microsoft Entra ID is Microsoft's cloud identity and access management platform.

It manages:

* Users
* Groups
* Authentication
* MFA
* Conditional Access
* Enterprise applications
* Administrative roles
* Guest users
* Identity protection

Simplified authentication flow:

```text
User
 ↓
Entra ID
 ↓
Authentication
 ↓
MFA
 ↓
Conditional Access
 ↓
Application Access
```

### Support areas

Common issues include:

* Password problems
* MFA issues
* Account lockout
* Sign-in failures
* Conditional Access blocks
* Guest access problems
* Application access problems

---

# 8. Microsoft Intune

Microsoft Intune is a cloud-based endpoint management service.

It manages:

* Devices
* Applications
* Configuration
* Compliance
* Endpoint security

Supported platforms include:

* Windows
* macOS
* iOS/iPadOS
* Android

Simplified model:

```text
Entra ID
    │
    ▼
Identity
    │
    ▼
Intune
    │
    ├── Enrollment
    ├── Configuration
    ├── Compliance
    ├── Applications
    └── Security
         │
         ▼
       Device
```

### Support areas

Common issues include:

* Enrollment failure
* Device not appearing
* Non-compliance
* Policy not applying
* Application deployment failure
* Company Portal problems
* Configuration conflicts

---

# 9. Microsoft 365 Admin Center

The Microsoft 365 Admin Center provides administrative capabilities for managing Microsoft 365 organizations.

Administrators can perform tasks such as:

* User management
* License management
* Group management
* Service health monitoring
* Organization settings
* Reports
* Support requests
* Microsoft 365 configuration

A support engineer may use the Admin Center to investigate whether an issue is isolated to a user or related to a broader service problem.

---

# 10. Microsoft Defender

Microsoft Defender provides security capabilities across Microsoft environments.

Important Defender services include:

* Defender for Office 365
* Defender for Endpoint
* Defender for Identity
* Defender for Cloud Apps

Security investigations can involve:

* Alerts
* Incidents
* Threats
* Email protection
* Endpoint protection
* Identity protection

---

# 11. Defender for Office 365

Defender for Office 365 provides protection for email and collaboration workloads.

It helps protect against threats such as:

* Phishing
* Malicious links
* Malicious attachments
* Business email compromise
* Malware

Important capabilities include:

* Safe Links
* Safe Attachments
* Anti-phishing
* Threat investigation
* Quarantine

### Support scenario

> User reports that a legitimate email is missing.

Investigation may include:

```text
Mailbox
 ↓
Message Trace
 ↓
Spam / Quarantine
 ↓
Defender Detection
 ↓
Policy
 ↓
Resolution
```

---

# 12. Defender for Endpoint

Defender for Endpoint provides endpoint security and threat detection capabilities.

It can help organizations:

* Detect threats
* Investigate incidents
* Monitor endpoints
* Respond to security events
* Protect devices

It can work alongside Intune for endpoint management and security.

---

# 13. Microsoft Purview

Microsoft Purview provides data governance, information protection, risk, audit, and compliance capabilities.

Important areas include:

* Data Loss Prevention
* Retention
* Retention labels
* Sensitivity labels
* eDiscovery
* Audit
* Information governance
* Insider risk capabilities

Simplified model:

```text
Microsoft 365 Data
       ↓
Microsoft Purview
       ↓
┌──────┼────────┬─────────┐
DLP  Retention  Labels   Audit
```

---

# 14. Microsoft 365 Copilot

Microsoft 365 Copilot provides AI capabilities integrated with Microsoft 365 applications.

It can work within applications such as:

* Outlook
* Teams
* Word
* Excel
* PowerPoint
* OneNote

From a support perspective, important concepts include:

* Licensing
* User eligibility
* Permissions
* Data access
* Microsoft 365 service configuration
* Security and compliance

A support engineer should understand that Copilot's usefulness depends on the user's authorized access to organizational data.

---

# 15. Power Platform

Microsoft Power Platform provides low-code and automation capabilities.

Major products include:

* Power Apps
* Power Automate
* Power BI
* Power Pages
* Dataverse

Example:

```text
User submits request
        ↓
Power Apps
        ↓
Power Automate
        ↓
Approval
        ↓
Teams / Email
        ↓
Record stored
```

Power Platform can be used to automate repetitive business processes.

---

# 16. Microsoft 365 Groups

Microsoft 365 Groups provide a membership and collaboration model used across Microsoft services.

Depending on how they are used, groups can be associated with services such as:

* Outlook
* Exchange
* Teams
* SharePoint

Simplified model:

```text
Microsoft 365 Group
       │
       ├── Members
       ├── Shared Mailbox
       ├── Calendar
       ├── SharePoint Site
       └── Collaboration
```

---

# 17. Microsoft 365 Service Health

Service Health is important for technical support.

Before troubleshooting a single user's application, determine whether Microsoft is already reporting an incident affecting the service.

Example:

```text
User reports problem
        ↓
Determine affected service
        ↓
Check Service Health
        ↓
┌─────────────────────┐
│ Known service issue?│
└──────────┬──────────┘
           │
       ┌───┴───┐
      YES      NO
       │        │
       ▼        ▼
Monitor    Troubleshoot
incident   user/service
```

This prevents support engineers from performing unnecessary troubleshooting when the root cause is a service-side incident.

---

# 18. Service Dependency Example

Consider a user opening Outlook.

A simplified dependency chain may be:

```text
User
 ↓
Device
 ↓
Internet
 ↓
Entra ID
 ↓
Authentication
 ↓
License
 ↓
Exchange Online
 ↓
Mailbox
 ↓
Outlook
```

If Outlook fails, the engineer should determine which layer is failing.

---

# 19. Cross-Service Troubleshooting

Microsoft 365 troubleshooting often crosses multiple services.

### Example

A user cannot access a SharePoint document from Teams.

Possible dependency chain:

```text
Teams
 ↓
Authentication
 ↓
Entra ID
 ↓
Conditional Access
 ↓
SharePoint
 ↓
Permissions
 ↓
Document Library
 ↓
File
```

Therefore, troubleshooting Teams alone may not solve the problem.

---

# 20. L1 vs L2 Support Perspective

### L1 Support

Typical responsibilities:

* Basic troubleshooting
* Password reset
* Application restart
* Basic configuration
* User guidance
* Ticket documentation
* Standard procedures

### L2 Support

Typically involves deeper investigation such as:

* Authentication analysis
* Service health investigation
* Exchange troubleshooting
* Entra ID investigation
* Conditional Access analysis
* Intune policy investigation
* Mail-flow troubleshooting
* Permissions analysis
* Log analysis
* PowerShell investigation
* Root-cause identification
* Escalation to specialist teams when required

---

# 21. Service-to-Support Mapping

| Service         | Primary Purpose           | Common Support Area                        |
| --------------- | ------------------------- | ------------------------------------------ |
| Outlook         | Email client              | Profiles, authentication, connectivity     |
| Exchange Online | Email service             | Mail flow, mailboxes, NDRs                 |
| Teams           | Collaboration             | Meetings, calls, login, audio/video        |
| SharePoint      | Content collaboration     | Permissions, sites, sharing                |
| OneDrive        | Personal business storage | Sync, storage, sharing                     |
| Entra ID        | Identity                  | Login, MFA, Conditional Access             |
| Intune          | Endpoint management       | Enrollment, compliance, policies           |
| Defender        | Security                  | Alerts, threats, email/device protection   |
| Purview         | Compliance                | DLP, retention, labels, audit              |
| Copilot         | AI productivity           | Licensing, access, application integration |
| Power Platform  | Automation                | Apps, flows, connectors                    |

---

# 22. Common Interview Questions

### Q1. What are the major Microsoft 365 services?

Major services include Exchange Online, Outlook, Teams, SharePoint Online, OneDrive, Microsoft Entra ID, Microsoft Intune, Microsoft Defender, Microsoft Purview, Microsoft 365 Copilot, and Power Platform.

### Q2. What is the difference between Outlook and Exchange Online?

Outlook is primarily a client application used by users to access email, calendar, and related functionality. Exchange Online is the cloud-hosted backend service that provides mailboxes, mail flow, calendaring, and related messaging services.

### Q3. What is the relationship between Teams and SharePoint?

Teams uses SharePoint for file storage associated with Teams and channels. Therefore, a Teams file-access problem can sometimes require investigation of SharePoint permissions or configuration.

### Q4. What is the relationship between OneDrive and SharePoint?

OneDrive for Business provides individual user file storage, while SharePoint provides organizational and collaborative content management. Both use Microsoft's cloud storage and collaboration capabilities.

### Q5. What is the relationship between Entra ID and Intune?

Entra ID provides identity and access capabilities, while Intune provides endpoint management. They work together for device identity, enrollment, compliance, and access control scenarios.

### Q6. Why should Service Health be checked during troubleshooting?

Because an issue may be caused by a Microsoft service incident rather than the user's device or application. Checking Service Health helps determine the scope and avoid unnecessary troubleshooting.

---

# 23. Key Takeaways

The most important concepts from this section are:

1. Microsoft 365 consists of multiple interconnected services.
2. Outlook is a client; Exchange Online provides the cloud messaging service.
3. Teams provides communication and collaboration.
4. SharePoint provides content and document collaboration.
5. OneDrive provides individual business file storage.
6. Entra ID provides identity and access capabilities.
7. Intune provides endpoint management.
8. Defender provides security capabilities.
9. Purview provides compliance and data governance capabilities.
10. Copilot provides AI-powered productivity capabilities.
11. Power Platform provides low-code applications and automation.
12. Service Health should be considered during incident investigation.
13. L2 support requires understanding cross-service dependencies.

---

## 24. Portfolio Learning Outcome

After completing this topic, I should be able to:

* Identify major Microsoft 365 services.
* Explain the purpose of each service.
* Explain basic service dependencies.
* Identify the correct service to investigate for a user issue.
* Understand the difference between client applications and backend services.
* Perform structured cross-service troubleshooting.
* Explain Microsoft 365 services during technical interviews.

---

## Next Topic

**Microsoft 365 Admin Center**

The next document will cover the administration portal, navigation, user management, licenses, groups, service health, reports, support requests, roles, and the types of tasks an L1/L2 support engineer may perform.
