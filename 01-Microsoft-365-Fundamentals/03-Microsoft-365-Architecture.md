# Microsoft 365 Architecture

## 1. Overview

Microsoft 365 is a cloud-based ecosystem made up of multiple services that work together to provide productivity, collaboration, identity, security, endpoint management, and compliance capabilities.

For an IT Support or L2 Support Engineer, understanding the architecture is important because a user-facing problem in one application can be caused by another underlying service.

For example:

```text
User cannot access Microsoft Teams
        ↓
Identity
        ↓
Authentication
        ↓
MFA / Conditional Access
        ↓
License
        ↓
Teams Service
        ↓
Teams Client
        ↓
Network / Device
```

Therefore, Microsoft 365 troubleshooting should consider the complete service dependency rather than only the application where the problem appears.

---

# 2. High-Level Architecture

A simplified Microsoft 365 architecture can be represented as:

```text
                         INTERNET
                            │
                            ▼
                    Microsoft Cloud
                            │
              ┌─────────────┴─────────────┐
              │                           │
              ▼                           ▼
       Microsoft Entra ID          Microsoft 365 Services
              │                           │
       ┌──────┼──────┐          ┌─────────┼─────────┐
       │      │      │          │         │         │
      MFA    CA    SSPR       Exchange   Teams   SharePoint
       │      │      │          │         │         │
       └──────┴──────┘          │         │         │
              │                 │         │         │
              ▼                 ▼         ▼         ▼
          User Access        Outlook    Teams    OneDrive
              │
              ▼
       Device / Endpoint
              │
              ▼
           Intune
              │
       ┌──────┴──────┐
       │             │
       ▼             ▼
   Compliance    Configuration
       │             │
       └──────┬──────┘
              ▼
        Conditional Access
```

This is a simplified conceptual model rather than a complete representation of Microsoft's internal cloud architecture.

---

# 3. Major Architecture Layers

The Microsoft 365 environment can be understood through several major layers.

## Layer 1 — Identity

Identity is the foundation for accessing Microsoft cloud services.

The primary identity platform is:

**Microsoft Entra ID**

It manages:

* Users
* Groups
* Authentication
* MFA
* Conditional Access
* Enterprise applications
* Administrative roles
* Guest identities
* Sign-in information

Basic flow:

```text
User
 ↓
Microsoft Entra ID
 ↓
Authentication
 ↓
MFA / Conditional Access
 ↓
Access Token
 ↓
Microsoft 365 Service
```

---

# 4. Layer 2 — Productivity Applications

Microsoft 365 provides applications used for business productivity.

Examples:

* Word
* Excel
* PowerPoint
* Outlook
* OneNote

These applications interact with Microsoft cloud services.

For example:

```text
Outlook
   ↓
Exchange Online
   ↓
User Mailbox
```

---

# 5. Layer 3 — Collaboration Services

Microsoft 365 provides several collaboration platforms.

### Microsoft Teams

Used for:

* Chat
* Meetings
* Calling
* Collaboration
* Teams and channels
* File collaboration

### SharePoint Online

Used for:

* Sites
* Document libraries
* Lists
* Pages
* Content collaboration

### OneDrive for Business

Used primarily for individual business file storage and synchronization.

A simplified relationship is:

```text
Microsoft Teams
       │
       ├── Chat
       ├── Meetings
       ├── Channels
       │
       └── Files
             │
             ▼
       SharePoint Online

User Files
     │
     ▼
OneDrive
```

---

# 6. Layer 4 — Exchange Online

Exchange Online provides cloud-based email and calendaring.

Major components include:

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

Simplified email flow:

```text
Sender
  ↓
Microsoft 365
  ↓
Exchange Online
  ↓
Mail Flow Processing
  ↓
Recipient Mailbox
  ↓
Outlook
```

When troubleshooting email, an engineer may need to investigate several layers rather than only Outlook.

---

# 7. Layer 5 — Endpoint Management

Microsoft Intune provides cloud-based endpoint management.

It can manage:

* Windows
* macOS
* iOS/iPadOS
* Android

Important Intune concepts include:

* Device enrollment
* Configuration profiles
* Compliance policies
* Application management
* Device actions
* Endpoint security
* Windows Autopilot

Simplified relationship:

```text
User
 ↓
Microsoft Entra ID
 ↓
Device Enrollment
 ↓
Microsoft Intune
 ↓
Configuration + Compliance
 ↓
Device
```

---

# 8. Layer 6 — Security

Microsoft security services protect identities, devices, applications, email, and data.

Examples include:

* Microsoft Defender
* Defender for Office 365
* Defender for Endpoint
* Defender for Identity
* Defender for Cloud Apps

Security can interact with identity and endpoint management.

For example:

```text
User
 ↓
Entra ID
 ↓
Conditional Access
 ↓
Device Compliance
 ↓
Intune
 ↓
Security Controls
 ↓
Application Access
```

---

# 9. Layer 7 — Compliance and Data Governance

Microsoft Purview provides capabilities for managing data governance and compliance.

Examples include:

* Data Loss Prevention
* Retention
* Retention labels
* Sensitivity labels
* eDiscovery
* Audit
* Information governance

Simplified relationship:

```text
Microsoft 365 Data
       │
       ▼
Microsoft Purview
       │
 ┌─────┼───────────┐
 │     │           │
DLP  Retention   Audit
 │     │           │
 └─────┼───────────┘
       ▼
Data Governance
```

---

# 10. Licensing Layer

Licensing determines which products and features an organization has access to.

A simplified model is:

```text
User
 ↓
Assigned License
 ↓
Available Services
 ↓
Service Features
```

However, having a license does not automatically mean that every action is permitted.

Access can also depend on:

* User permissions
* Group membership
* Administrative roles
* Conditional Access
* Application policies
* Device compliance
* Service configuration

Therefore:

```text
License ≠ Automatic Access to Everything
```

---

# 11. Authentication and Authorization

Two important concepts are:

### Authentication

Determines:

> "Who are you?"

Examples:

* Username and password
* MFA
* Passwordless authentication

### Authorization

Determines:

> "What are you allowed to access?"

Examples:

* SharePoint permissions
* Teams policies
* Administrative roles
* Application permissions

Simplified flow:

```text
User
 ↓
Authentication
 ↓
Identity Verified
 ↓
Authorization
 ↓
Access Granted / Denied
```

---

# 12. Conditional Access

Conditional Access allows organizations to make access decisions based on conditions.

Conditions can include factors such as:

* User
* Group
* Application
* Device
* Location
* Risk
* Authentication strength

Simplified model:

```text
User attempts access
        ↓
Authentication
        ↓
Conditional Access Evaluation
        ↓
┌───────────────┬───────────────┐
│               │               │
Allow         Require          Block
              MFA
              │
              ▼
         Device Compliance
```

Conditional Access is therefore an important consideration when a user suddenly loses access to a Microsoft 365 service.

---

# 13. Service Dependencies

Microsoft 365 services are interconnected.

A simplified dependency model is:

```text
                    Microsoft Entra ID
                           │
                 ┌─────────┼─────────┐
                 │         │         │
                 ▼         ▼         ▼
               Users      MFA       CA
                 │
                 ▼
              Licensing
                 │
        ┌────────┼────────┐
        │        │        │
        ▼        ▼        ▼
    Exchange   Teams   SharePoint
        │        │        │
        ▼        ▼        ▼
    Outlook   Teams    OneDrive
                         │
                         ▼
                      Intune
                         │
                         ▼
                    Device State
```

This model helps explain why troubleshooting one application may require checking multiple services.

---

# 14. Example — Outlook Troubleshooting Architecture

Suppose a user reports:

> "Outlook keeps asking me for my password."

A support engineer should consider:

```text
User
 ↓
Entra ID
 ↓
Authentication
 ↓
MFA / Conditional Access
 ↓
License
 ↓
Exchange Online
 ↓
Mailbox
 ↓
Autodiscover
 ↓
Outlook Profile
 ↓
Credential / Token State
 ↓
Network
```

Possible causes include:

* Authentication problems
* Expired or invalid authentication state
* Conditional Access
* Outlook profile issues
* Autodiscover problems
* Connectivity problems
* Service-side issues

---

# 15. Example — Teams Troubleshooting Architecture

User reports:

> "Teams is not allowing me to sign in."

Investigation:

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
License
 ↓
Teams Service
 ↓
Teams Client
 ↓
Device
 ↓
Network
```

The engineer should determine where the failure occurs before applying a fix.

---

# 16. Example — OneDrive Troubleshooting Architecture

User reports:

> "OneDrive is not syncing."

Investigation:

```text
User
 ↓
Entra ID
 ↓
Authentication
 ↓
OneDrive Service
 ↓
SharePoint Online
 ↓
Storage / Permissions
 ↓
OneDrive Client
 ↓
Device
 ↓
Network
```

Possible causes include:

* Authentication
* Storage limitations
* File restrictions
* Permission problems
* Client issues
* Network problems
* Service-side problems

---

# 17. Example — Intune and Conditional Access

Consider a company that requires compliant devices to access corporate resources.

The flow may look like:

```text
User
 ↓
Entra ID Authentication
 ↓
Conditional Access
 ↓
Check Device
 ↓
Intune Compliance Status
 ↓
Compliant?
 ├── YES → Access
 │
 └── NO → Block / Require Remediation
```

This demonstrates the relationship between:

* Entra ID
* Conditional Access
* Intune
* Device compliance
* Microsoft 365 applications

---

# 18. Microsoft 365 Troubleshooting Model

A useful troubleshooting model is:

```text
                    User Issue
                        │
                        ▼
                  Identify Scope
                        │
              ┌─────────┴─────────┐
              │                   │
           One User           Multiple Users
              │                   │
              ▼                   ▼
        User / Device       Service Health
        Investigation          / Outage
              │
              ▼
          Identity
              │
              ▼
       Authentication
              │
              ▼
       License / Access
              │
              ▼
          Policy
              │
              ▼
        Application
              │
              ▼
          Network
              │
              ▼
         Resolution
              │
              ▼
          Validation
              │
              ▼
        Documentation
```

---

# 19. Why Architecture Matters for L2 Support

An L2 support engineer should not troubleshoot only at the application layer.

For example:

> "Teams isn't working."

A basic approach might be:

```text
Restart Teams
Reinstall Teams
```

A stronger L2 approach is:

```text
Define the problem
       ↓
Determine scope
       ↓
Check service health
       ↓
Check identity
       ↓
Check authentication
       ↓
Check MFA / Conditional Access
       ↓
Check licensing
       ↓
Check Teams policies
       ↓
Check client
       ↓
Check device
       ↓
Check network
       ↓
Resolve
       ↓
Validate
       ↓
Document
```

This approach helps prevent unnecessary application reinstalls when the actual problem is identity, policy, licensing, or service availability.

---

# 20. Key Takeaways

The major architectural concepts to remember are:

1. Microsoft 365 is a collection of integrated cloud services.
2. Microsoft Entra ID provides identity and access capabilities.
3. Exchange Online provides email and calendaring.
4. Teams provides communication and collaboration.
5. SharePoint provides content and collaboration capabilities.
6. OneDrive provides individual business file storage and synchronization.
7. Intune manages endpoints and device compliance.
8. Defender provides security capabilities.
9. Purview provides compliance and information governance capabilities.
10. Licensing determines available products and features.
11. Conditional Access can control access based on conditions.
12. Microsoft 365 services have dependencies.
13. Effective L2 troubleshooting requires understanding those dependencies.

---

# 21. Interview Questions

### Q1. Explain Microsoft 365 architecture.

Microsoft 365 is an integrated cloud ecosystem consisting of productivity, collaboration, identity, endpoint management, security, and compliance services. Microsoft Entra ID provides identity and access capabilities, Exchange Online handles email, Teams handles collaboration, SharePoint and OneDrive handle content and files, Intune manages endpoints, and Microsoft security and compliance services protect organizational resources and data.

### Q2. Why is Entra ID important in Microsoft 365?

Entra ID provides identity and access capabilities for Microsoft cloud services. It supports authentication, MFA, Conditional Access, user and group management, application access, and administrative roles.

### Q3. How does Intune work with Entra ID?

Entra ID provides identity and access capabilities while Intune manages devices, applications, configurations, and compliance. Conditional Access can use Intune device compliance information when making access decisions.

### Q4. A user cannot access Teams. Is it always a Teams problem?

No. The issue could be related to identity, authentication, MFA, Conditional Access, licensing, Teams policies, device configuration, network connectivity, or Microsoft service health.

### Q5. Why should an L2 engineer understand service dependencies?

Because an application issue can originate from an underlying service. Understanding dependencies allows the engineer to identify the actual root cause instead of applying generic application-level fixes.

---

# 22. Portfolio Learning Outcome

After studying this architecture, I should be able to:

* Explain the major Microsoft 365 services.
* Explain how identity connects to Microsoft 365.
* Understand authentication and authorization.
* Understand the relationship between Intune and Entra ID.
* Understand the role of Conditional Access.
* Understand major service dependencies.
* Approach Microsoft 365 incidents systematically.
* Troubleshoot beyond the application layer.
* Explain Microsoft 365 architecture during technical interviews.
