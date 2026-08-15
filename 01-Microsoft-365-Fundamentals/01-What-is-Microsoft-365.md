# What is Microsoft 365?

## 1. Overview

Microsoft 365 is Microsoft's cloud-based productivity and collaboration platform that combines applications, cloud services, identity, security, device management, and collaboration capabilities for organizations.

It provides users with access to services such as:

* Microsoft Outlook
* Exchange Online
* Microsoft Teams
* SharePoint Online
* OneDrive for Business
* Microsoft Entra ID
* Microsoft Intune
* Microsoft Defender
* Microsoft Purview
* Microsoft 365 Copilot
* Power Platform

From an IT support perspective, Microsoft 365 is not just a collection of Office applications. It is an integrated cloud ecosystem where identity, licensing, security, devices, applications, and data are interconnected.

---

## 2. Microsoft 365 vs Traditional Office

Traditional Office deployments primarily focused on installing productivity applications such as Word, Excel, PowerPoint, and Outlook on a computer.

Microsoft 365 extends beyond desktop applications.

It provides:

```text
Applications
     +
Cloud Services
     +
Identity
     +
Security
     +
Device Management
     +
Collaboration
     +
Compliance
     +
Automation
```

This allows organizations to manage users, devices, applications, data, security, and collaboration through cloud-based services.

---

## 3. Major Microsoft 365 Components

### Productivity Applications

Microsoft 365 includes applications used for everyday business productivity.

Examples:

* Word
* Excel
* PowerPoint
* Outlook
* OneNote

### Collaboration

Microsoft 365 enables employees to collaborate through:

* Microsoft Teams
* SharePoint
* OneDrive
* Outlook
* Microsoft 365 Groups

### Email

Exchange Online provides cloud-hosted business email.

It supports:

* User mailboxes
* Shared mailboxes
* Distribution groups
* Calendars
* Mail flow
* Anti-spam protection
* Anti-malware protection
* Message trace

### Identity

Microsoft Entra ID provides identity and access capabilities.

It manages:

* Users
* Groups
* Authentication
* MFA
* Conditional Access
* Applications
* Administrative roles

### Endpoint Management

Microsoft Intune provides cloud-based endpoint management.

It can manage:

* Windows devices
* macOS devices
* iOS/iPadOS devices
* Android devices
* Applications
* Configuration policies
* Compliance policies
* Endpoint security

### Security

Microsoft Defender provides security capabilities across Microsoft environments.

Examples include:

* Defender for Office 365
* Defender for Endpoint
* Defender for Identity
* Defender for Cloud Apps

### Compliance

Microsoft Purview provides data governance, compliance, and information protection capabilities.

Examples include:

* Data Loss Prevention
* Retention
* Sensitivity Labels
* eDiscovery
* Audit
* Information Governance

---

## 4. High-Level Microsoft 365 Architecture

A simplified Microsoft 365 environment can be viewed as:

```text
                         Microsoft 365
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
       Identity          Applications          Security
          │                   │                   │
   Microsoft Entra ID    Outlook              Defender
          │              Teams                  │
          │              SharePoint             │
          │              OneDrive               │
          │                                      │
          └───────────────┬──────────────────────┘
                          │
                    Device Management
                          │
                       Intune
                          │
                       Devices
```

These services are integrated rather than operating completely independently.

---

## 5. Microsoft 365 Tenant

An organization normally has a Microsoft 365 tenant.

The tenant represents the organization's Microsoft cloud environment.

It contains resources such as:

* Users
* Groups
* Licenses
* Domains
* Applications
* Policies
* Security settings
* Microsoft 365 services

For example:

```text
Organization
      │
      ▼
Microsoft 365 Tenant
      │
      ├── Users
      ├── Groups
      ├── Licenses
      ├── Exchange Online
      ├── Teams
      ├── SharePoint
      ├── OneDrive
      ├── Intune
      ├── Entra ID
      └── Security / Compliance
```

---

## 6. How Identity Connects Microsoft 365 Services

A user's Microsoft 365 experience generally begins with identity.

For example:

```text
User
 ↓
Microsoft Entra ID
 ↓
Authentication
 ↓
MFA / Conditional Access
 ↓
License Verification
 ↓
Application / Service Access
 ↓
Exchange / Teams / SharePoint / OneDrive
```

This is important for troubleshooting.

For example, if a user cannot access Microsoft Teams, the issue may not necessarily be a Teams application problem.

Possible causes could include:

* Account disabled
* Authentication failure
* MFA problem
* Conditional Access policy
* Missing license
* Teams policy
* Network problem
* Service outage
* Application issue

Therefore, an IT support engineer should troubleshoot the complete service dependency chain.

---

## 7. Microsoft 365 Administration

Microsoft 365 administrators can manage many organizational settings through administrative portals.

Common administrative tasks include:

* Creating users
* Managing groups
* Assigning licenses
* Managing roles
* Configuring domains
* Monitoring service health
* Reviewing reports
* Managing security settings
* Managing Exchange Online
* Managing Teams
* Managing SharePoint
* Managing OneDrive
* Managing Intune

---

## 8. Microsoft 365 Licensing

Microsoft 365 uses subscription-based licensing.

Licensing determines which services and features a user or organization can access.

A support engineer should understand that:

```text
User Account
     +
License
     +
Permissions
     +
Policies
     =
Service Access
```

Therefore, when a user cannot access a service, licensing should be considered as part of troubleshooting.

---

## 9. Microsoft 365 and IT Support

Microsoft 365 creates a wide range of enterprise support incidents.

Common examples include:

### Outlook

> User cannot send or receive email.

Possible areas to investigate:

* Outlook profile
* Authentication
* Exchange Online
* Mailbox
* Network
* Service health

### Teams

> User cannot join a meeting.

Possible areas to investigate:

* Authentication
* Teams client
* Meeting policy
* Network
* Permissions
* Service health

### OneDrive

> User's files are not synchronizing.

Possible areas to investigate:

* OneDrive client
* Authentication
* Storage
* File restrictions
* Network
* Sync status

### SharePoint

> User receives "Access Denied."

Possible areas to investigate:

* SharePoint permissions
* Group membership
* Sharing configuration
* Conditional Access
* Authentication

### Intune

> Device is showing as non-compliant.

Possible areas to investigate:

* Compliance policy
* Device enrollment
* Configuration
* Security requirements
* User/device association

---

## 10. Example Enterprise Support Flow

Consider an employee who reports:

> "I cannot access Microsoft Teams."

A structured investigation could be:

```text
1. Confirm the user's identity
        ↓
2. Check whether the account is active
        ↓
3. Check authentication
        ↓
4. Check MFA
        ↓
5. Check Conditional Access
        ↓
6. Check Microsoft 365 license
        ↓
7. Check Teams policies
        ↓
8. Check Teams client
        ↓
9. Check network connectivity
        ↓
10. Check Microsoft 365 Service Health
        ↓
11. Apply resolution
        ↓
12. Validate access
        ↓
13. Document the incident
```

This demonstrates why understanding the Microsoft 365 ecosystem is important for an L2 support engineer.

---

## 11. Key Skills Demonstrated

Through studying Microsoft 365, an IT support engineer can develop knowledge in:

* Cloud services
* Identity management
* Authentication
* Access management
* Email administration
* Collaboration platforms
* Endpoint management
* Security
* Compliance
* Troubleshooting
* Incident management
* Automation
* PowerShell

---

## 12. Key Takeaways

Microsoft 365 should be viewed as an integrated cloud ecosystem rather than simply a collection of Office applications.

The most important concepts to understand are:

1. Microsoft 365 provides cloud-based productivity and business services.
2. Microsoft Entra ID provides identity and access capabilities.
3. Exchange Online provides cloud email services.
4. Teams provides communication and collaboration.
5. SharePoint provides content and collaboration capabilities.
6. OneDrive provides personal business file storage and synchronization.
7. Intune provides endpoint management.
8. Defender provides security capabilities.
9. Purview provides compliance and information governance capabilities.
10. Licensing and permissions affect service access.
11. Microsoft 365 services are interconnected.
12. Effective troubleshooting requires understanding those dependencies.

---

## 13. Interview Questions

### Basic

**Q: What is Microsoft 365?**

Microsoft 365 is Microsoft's cloud-based productivity and business platform that provides applications and services for productivity, collaboration, identity, security, device management, and compliance.

**Q: Is Microsoft 365 only Office applications?**

No. Microsoft 365 includes productivity applications as well as cloud services such as Exchange Online, Teams, SharePoint, OneDrive, Microsoft Entra ID, Intune, Defender, and Purview.

**Q: What is a Microsoft 365 tenant?**

A Microsoft 365 tenant is an organization's dedicated cloud environment containing its users, groups, licenses, domains, services, applications, policies, and configurations.

**Q: Why is Microsoft Entra ID important in Microsoft 365?**

Microsoft Entra ID provides identity and access capabilities that are used to authenticate users and control access to Microsoft cloud services.

### Scenario-Based

**Q: A user cannot access Teams. What would you check?**

I would first identify whether the issue affects only the user or multiple users. Then I would check the user's account status, authentication, MFA, Conditional Access, licensing, Teams policies, client application, network connectivity, and Microsoft 365 service health before applying and validating the resolution.

---

## 14. Portfolio Note

This document provides the foundational understanding required before moving into individual Microsoft 365 services.

The next topics in this section explore the differences between Microsoft 365 and Office 365, Microsoft 365 architecture, services, tenants, administration, licensing, and common support scenarios.
