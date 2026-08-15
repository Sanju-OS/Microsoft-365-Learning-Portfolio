# Microsoft 365 Licensing and Subscriptions

## 1. Overview

Microsoft 365 licensing determines which Microsoft cloud products and services a user or organization is entitled to use.

A simple model is:

Organization
     ↓
Microsoft 365 Subscription
     ↓
License
     ↓
Service Plans
     ↓
User
     ↓
Available Services

Licensing is important for Microsoft 365 administrators and support engineers because many user-access issues are caused by missing, incorrect, expired, or misconfigured licenses.

---

# 2. Subscription vs License

These terms are related but different.

## Subscription

A subscription is the organization's purchased Microsoft service plan.

Example:

Microsoft 365 Business Premium

## License

A license is an entitlement that can be assigned to a user.

Example:

User receives a Microsoft 365 license.

Simplified:

Subscription
     ↓
Licensing Entitlements
     ↓
User Assignment
     ↓
Service Access

---

# 3. Service Plans

A Microsoft 365 license can contain multiple service plans.

A simplified example:

License
   │
   ├── Exchange Online
   ├── SharePoint Online
   ├── Teams
   └── OneDrive

The exact services available depend on the specific license.

Therefore:

User has a license

does not always mean:

User has every Microsoft 365 service enabled.

---

# 4. Common Microsoft 365 License Families

Microsoft offers different licensing options for different organization sizes and requirements.

Common families include:

- Microsoft 365 Business
- Microsoft 365 Enterprise
- Microsoft 365 Education
- Microsoft 365 Frontline

Examples of well-known plans include:

- Microsoft 365 Business Basic
- Microsoft 365 Business Standard
- Microsoft 365 Business Premium
- Microsoft 365 E3
- Microsoft 365 E5

The exact features and pricing can change over time, so administrators should always verify current Microsoft licensing documentation.

---

# 5. Business Basic

Microsoft 365 Business Basic is designed primarily around cloud services.

Depending on the current plan configuration, it can provide services such as:

- Exchange Online
- OneDrive
- SharePoint
- Microsoft Teams
- Web and mobile Office applications

A key point:

Business Basic is not the same as Business Standard.

---

# 6. Business Standard

Business Standard generally includes the cloud services available in Business Basic plus desktop Office applications.

A simplified comparison:

Business Basic
    ↓
Cloud services
    +
Web/mobile Office apps

Business Standard
    ↓
Cloud services
    +
Desktop Office applications

Always verify the current Microsoft feature matrix before making licensing decisions.

---

# 7. Business Premium

Business Premium is designed for organizations that need additional security and device-management capabilities along with Microsoft 365 productivity services.

Depending on the current licensing configuration, it can include capabilities related to:

- Microsoft Intune
- Microsoft Defender
- Device management
- Endpoint security
- Identity and access protection

This makes it particularly relevant to modern workplace and endpoint-support environments.

---

# 8. Enterprise Licensing

Enterprise plans are designed for larger or more complex organizations.

Examples include:

- Microsoft 365 E3
- Microsoft 365 E5

Enterprise environments can provide broader capabilities around:

- Productivity
- Security
- Compliance
- Identity
- Device management
- Analytics

The exact feature set depends on the specific plan.

---

# 9. E3 vs E5

A simplified way to understand these plans:

E3
 ↓
Enterprise productivity
 +
Security/compliance capabilities

E5
 ↓
E3-level capabilities
 +
Additional advanced security/compliance/analytics capabilities

Do not assume every E5 feature is automatically enabled. Licensing entitlement and tenant configuration are separate considerations.

---

# 10. License Assignment

A license can be assigned to a user.

Example:

User
 ↓
Microsoft 365 License
 ↓
Exchange Online
 ↓
Mailbox
 ↓
Outlook

Another example:

User
 ↓
License
 ↓
SharePoint
 ↓
OneDrive

---

# 11. Direct License Assignment

A license can be assigned directly to an individual user.

Example:

```text
John
 ↓
Microsoft 365 License
````

This is easy to understand but can become difficult to manage in large organizations.

Example:

```text
10,000 Users
      ↓
Individual License Management
      ↓
Large Administrative Workload
```

---

# 12. Group-Based Licensing

Organizations can use groups to simplify licensing.

Example:

```text
IT Users
   ↓
Group-Based License
   ↓
Microsoft 365 License
   ↓
IT Employees
```

When a user is added to the appropriate group, the licensing assignment can be applied according to the configured rules.

This can improve consistency and reduce manual administration.

---

# 13. Direct vs Group-Based Licensing

| Method      | Description                              |
| ----------- | ---------------------------------------- |
| Direct      | License assigned directly to a user      |
| Group-based | License associated with group membership |

### Direct

```text
User
 ↓
License
```

### Group-Based

```text
User
 ↓
Group
 ↓
License
```

Group-based licensing is generally easier to scale.

---

# 14. License Removal

If a license is removed from a user, services associated with that license may become unavailable.

Example:

```text
User
 ↓
License Removed
 ↓
Service Entitlement Changes
 ↓
Access May Be Lost
```

Administrators must understand the impact before removing licenses.

---

# 15. License Expiration

Subscriptions can have an expiration or renewal status.

A simplified model:

```text
Subscription
     ↓
Active
     ↓
Renewal / Expiration
     ↓
Grace / Disabled State
     ↓
Service Impact
```

The exact behavior depends on the subscription, billing arrangement, and Microsoft service policies.

---

# 16. Trial Licenses

Organizations may use trial subscriptions to evaluate Microsoft services.

Example:

```text
Trial
 ↓
Evaluation
 ↓
Decision
 ├── Purchase
 └── Allow Trial to End
```

Administrators should monitor trial subscriptions to prevent unexpected service interruptions.

---

# 17. License Conflict

A user may have multiple licenses or service plans that overlap.

Example:

```text
User
 ├── License A
 └── License B
       ↓
Overlapping Service Plans
```

This can require administrative review.

When troubleshooting licensing issues, check:

* Assigned licenses
* Service plans
* Assignment source
* Group membership
* License errors
* Conflicting plans

---

# 18. License Assignment Errors

License assignment can fail for several reasons.

Possible causes include:

* No available licenses
* Invalid license combination
* Service plan conflict
* Group-based assignment issue
* Directory synchronization issue
* Administrative configuration issue

Simplified troubleshooting:

```text
License Assignment
       ↓
Check Availability
       ↓
Check User
       ↓
Check Existing Licenses
       ↓
Check Service Plans
       ↓
Check Group Membership
       ↓
Check Assignment Errors
       ↓
Resolve
```

---

# 19. License vs Permission

Having a license does not necessarily mean the user has permission to access every resource.

Example:

```text
License
   ↓
Provides Service Entitlement

Permission
   ↓
Determines Resource Access
```

Therefore:

```text
User Has License
        ≠
User Has Permission to Every Resource
```

---

# 20. Example — Teams Access Issue

User reports:

> "I cannot use Microsoft Teams."

Possible investigation:

```text
User
 ↓
Account Enabled?
 ↓
License Assigned?
 ↓
Teams Service Plan Available?
 ↓
Teams Policy
 ↓
Conditional Access
 ↓
Application
 ↓
Device
```

The problem may be licensing, policy, identity, device, or service-related.

---

# 21. Example — OneDrive Access Issue

User reports:

> "My OneDrive is not available."

Investigation:

```text
User
 ↓
Account Status
 ↓
License
 ↓
OneDrive Service Plan
 ↓
SharePoint Online
 ↓
Provisioning
 ↓
Authentication
 ↓
Device / Client
```

Do not immediately assume the OneDrive client is the root cause.

---

# 22. Example — Outlook Mailbox Issue

User reports:

> "I cannot access my company mailbox."

Possible investigation:

```text
User
 ↓
Account
 ↓
Exchange Online License / Service Plan
 ↓
Mailbox
 ↓
Authentication
 ↓
Conditional Access
 ↓
Outlook
 ↓
Autodiscover
```

Licensing is only one part of the investigation.

---

# 23. License Troubleshooting Checklist

When a user reports a Microsoft 365 access issue:

### Step 1 — Identify User

```text
Who is affected?
```

### Step 2 — Check Account

```text
Is the account enabled?
```

### Step 3 — Check License

```text
Is the required license assigned?
```

### Step 4 — Check Service Plan

```text
Is the required service included/enabled?
```

### Step 5 — Check Assignment

```text
Was the license assigned directly or through a group?
```

### Step 6 — Check Errors

```text
Are there license assignment errors?
```

### Step 7 — Check Permissions

```text
Does the user actually have access to the resource?
```

### Step 8 — Validate

```text
Test the affected service again.
```

---

# 24. L1 Support Perspective

Depending on organizational permissions, L1 support may:

* Verify the user's license
* Check whether a license is assigned
* Confirm the affected service
* Check basic account status
* Collect screenshots/error messages
* Identify whether other users are affected
* Escalate licensing issues

---

# 25. L2 Support Perspective

L2 support may investigate:

* Service plans
* Group-based licensing
* Assignment errors
* License conflicts
* Identity synchronization
* Conditional Access
* Application access
* Tenant configuration
* Service health
* Root cause

---

# 26. License Troubleshooting Scenario

## Problem

> "A new employee can sign in but cannot use Outlook."

### Investigation

```text
New Employee
     ↓
User Account
     ↓
Account Enabled?
     ↓
License Assigned?
     ↓
Exchange Online Service Plan?
     ↓
Mailbox Provisioned?
     ↓
Authentication
     ↓
Outlook Configuration
     ↓
Autodiscover
     ↓
Test
```

### Possible Root Causes

* License not assigned
* Exchange Online service plan unavailable
* Provisioning delay
* Account issue
* Authentication problem
* Outlook configuration problem

---

# 27. License Troubleshooting Scenario

## Problem

> "User had access yesterday but cannot use the service today."

Investigation:

```text
User
 ↓
License Still Assigned?
 ↓
Group Membership
 ↓
License Assignment
 ↓
Service Plan
 ↓
Subscription Status
 ↓
Conditional Access
 ↓
Service Health
```

Possible causes include:

* License removed
* User removed from licensing group
* Subscription changed
* Service plan disabled
* Policy changed
* Service outage

---

# 28. License Management Best Practices

Organizations should:

* Use standardized licensing processes
* Avoid unnecessary direct assignments where scalable group-based management is appropriate
* Regularly review unused licenses
* Monitor subscription status
* Document licensing decisions
* Follow least privilege
* Review license assignment errors
* Avoid assigning unnecessary service plans
* Maintain accurate joiner/mover/leaver processes

---

# 29. Licensing and Joiner-Mover-Leaver

Licensing is closely connected to the user lifecycle.

### Joiner

```text
New Employee
 ↓
Create User
 ↓
Add to Appropriate Group
 ↓
License Assignment
 ↓
Service Access
```

### Mover

```text
Department Change
 ↓
Group Changes
 ↓
License Review
 ↓
Application Review
```

### Leaver

```text
Employee Leaves
 ↓
Disable Account
 ↓
Review License
 ↓
Remove / Reclaim License
 ↓
Handle Resources
```

---

# 30. Licensing and Cost Management

Licensing is also an important part of IT cost management.

Example:

```text
Purchased Licenses
       ↓
Assigned Licenses
       ↓
Active Users
       ↓
Unused Licenses
```

Organizations can review unused or unnecessary assignments to improve license utilization.

However, license removal should always consider business requirements and service/data retention implications.

---

# 31. Important Licensing Terms

| Term                  | Meaning                                             |
| --------------------- | --------------------------------------------------- |
| Subscription          | Purchased Microsoft service offering                |
| License               | User entitlement to products/services               |
| Service Plan          | Individual service capability within a license      |
| Direct Assignment     | License assigned directly to user                   |
| Group-Based Licensing | License assigned through group membership           |
| License Conflict      | Overlapping or incompatible licensing configuration |
| Assignment Error      | Failure to apply a license                          |
| Trial                 | Temporary evaluation subscription                   |
| Renewal               | Continuation of subscription                        |
| Expiration            | End of subscription period                          |

---

# 32. Interview Questions

## Q1. What is a Microsoft 365 license?

A Microsoft 365 license provides a user with entitlement to specific Microsoft products and services based on the purchased licensing plan.

---

## Q2. What is the difference between a subscription and a license?

A subscription is the organization's purchased service offering, while a license represents the entitlement that can be assigned to users.

---

## Q3. What is a service plan?

A service plan represents an individual service or capability included within a Microsoft 365 license.

---

## Q4. What is group-based licensing?

Group-based licensing allows licenses to be assigned based on group membership rather than manually assigning licenses to every user.

---

## Q5. A user has a Microsoft 365 license but cannot access Teams. What do you check?

I would check the assigned license, Teams-related service plan, account status, group-based licensing if applicable, Teams policies, Conditional Access, service health, and the client/device.

---

## Q6. Can a licensed user access every Microsoft 365 resource?

No. A license provides service entitlement, but resource access is also controlled by permissions, groups, policies, application assignments, and other security controls.

---

## Q7. What would you check if license assignment fails?

I would check license availability, the user's existing licenses, service-plan conflicts, group membership, assignment errors, synchronization issues, and administrative configuration.

---

## Q8. Why is group-based licensing useful?

It provides a scalable and consistent way to manage licensing based on organizational roles or groups and reduces manual administration.

---

# 33. Portfolio Learning Outcome

After completing this topic, I should be able to:

* Explain Microsoft 365 subscriptions.
* Explain licenses.
* Explain service plans.
* Understand common Microsoft 365 licensing families.
* Understand direct license assignment.
* Understand group-based licensing.
* Understand license conflicts.
* Understand license assignment errors.
* Distinguish licensing from permissions.
* Troubleshoot common licensing-related incidents.
* Understand licensing during Joiner-Mover-Leaver processes.
* Explain licensing concepts during technical interviews.
