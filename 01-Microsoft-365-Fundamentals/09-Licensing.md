# Microsoft 365 Licensing

## 1. Overview

Microsoft 365 licensing determines which Microsoft products, applications, and services a user is entitled to access.

A simple way to understand the relationship is:

```text
Organization
      ↓
Microsoft 365 Tenant
      ↓
Subscription
      ↓
Licenses
      ↓
User
      ↓
Services
````

Microsoft explains that an organization can have multiple subscriptions, and licenses from those subscriptions can be assigned to individual user accounts. The services available to a user depend on the licensing plan assigned to them.

---

# 2. Subscription vs License

These terms are related but different.

## Subscription

A subscription is the organization's purchased Microsoft service plan.

Example:

```text
Microsoft 365 E3 Subscription
```

## License

A license is an entitlement from the subscription that can be assigned to a user.

Example:

```text
Microsoft 365 E3
      ↓
100 Licenses
      ↓
100 Users can potentially be licensed
```

Microsoft describes the hierarchy as:

```text
Organization
    ↓
Subscriptions
    ↓
Licenses
    ↓
User Accounts
```

---

# 3. Simple Example

Suppose a company has:

```text
Microsoft 365 E3
100 licenses
```

The administrator can assign those licenses to users.

```text
E3 Subscription
       │
       ├── License → User A
       ├── License → User B
       ├── License → User C
       └── License → User D
```

The number of available licenses determines how many users can be assigned that entitlement.

---

# 4. Licensing Plan

A licensing plan defines the Microsoft 365 services available through that plan.

Examples of plans include:

* Microsoft 365 Business Basic
* Microsoft 365 Business Standard
* Microsoft 365 Business Premium
* Microsoft 365 E3
* Microsoft 365 E5
* Microsoft 365 Apps for business
* Microsoft 365 Apps for enterprise

The exact features and services depend on the specific plan.

---

# 5. Service Plans

A license can contain multiple individual service components.

For example:

```text
Microsoft 365 License
       │
       ├── Exchange Online
       ├── SharePoint Online
       ├── Microsoft Teams
       ├── OneDrive
       └── Microsoft 365 Apps
```

Microsoft refers to these individual components as service plans.

This distinction is important when troubleshooting licensing problems.

---

# 6. License Assignment

A license normally needs to be assigned to a user before that user can use the licensed Microsoft 365 services.

Example:

```text
User
 ↓
License Assigned
 ↓
Services Enabled
 ↓
User Can Access Services
```

Without the required license, the user may not have access to a particular Microsoft 365 service.

---

# 7. Direct License Assignment

An administrator can assign a license directly to a user.

Example:

```text
User: John
       ↓
Microsoft 365 E3
       ↓
License Assigned
```

This is simple for small environments.

However, manually assigning licenses to hundreds or thousands of users can become difficult to manage.

---

# 8. Group-Based Licensing

Organizations can also use groups to manage licensing.

Example:

```text
IT Employees
      ↓
Security Group
      ↓
Microsoft 365 License
      ↓
Group Members
```

When users are added to the appropriate group, licensing can be applied according to the organization's configuration.

This makes license management more scalable.

---

# 9. Direct vs Group-Based Licensing

| Method            | Description                                            |
| ----------------- | ------------------------------------------------------ |
| Direct Assignment | License assigned directly to a user                    |
| Group-Based       | License associated with a group and applied to members |

### Direct

```text
User → License
```

### Group-Based

```text
User → Group → License
```

---

# 10. License Availability

Administrators need to monitor how many licenses are:

* Purchased
* Assigned
* Available

Example:

```text
Total Licenses:     100
Assigned:            85
Available:           15
```

If all licenses are assigned:

```text
Total:       100
Assigned:    100
Available:     0
```

A new user may require an additional license or reassignment of an existing license.

---

# 11. License Reassignment

When an employee leaves the organization, their license may become available for reassignment according to the organization's process.

Example:

```text
Employee Leaves
       ↓
Account Offboarding
       ↓
License Recovered
       ↓
Available License
       ↓
New Employee
```

Microsoft documents that organizations can reassign licenses as their needs change.

---

# 12. License vs Permission

A license and a permission are not the same thing.

### License

Determines whether the user is entitled to use a service.

### Permission

Determines what the user can do within that service or resource.

Example:

```text
License
   ↓
Can use SharePoint
   ↓
Permission
   ↓
Can access specific SharePoint Site
```

Therefore:

```text
Licensed ≠ Automatically Authorized for Everything
```

---

# 13. License vs Group Membership

Group membership may affect access and licensing, but it does not automatically mean a user has every Microsoft 365 service.

Example:

```text
User
 ↓
IT Group
 ↓
Application Access
```

The user may still require an appropriate license for the application or service.

---

# 14. License and Exchange Online

When a user is assigned a license containing Exchange Online, the user's Exchange mailbox can be provisioned.

Simplified:

```text
User
 ↓
Microsoft 365 License
 ↓
Exchange Online Service
 ↓
Mailbox
```

Therefore, when troubleshooting a missing mailbox, licensing should be one of the checks.

---

# 15. License and SharePoint Online

If the user's license includes the required SharePoint Online service:

```text
User
 ↓
License
 ↓
SharePoint Online
 ↓
SharePoint Access
```

However, licensing alone does not necessarily grant access to every SharePoint site.

Site permissions and other access controls still apply.

---

# 16. License and Microsoft Teams

Microsoft Teams functionality depends on the user's licensing and organizational configuration.

Simplified:

```text
User
 ↓
License
 ↓
Teams Service
 ↓
Teams Access
```

If a user reports that Teams functionality is unavailable, licensing is one of the checks an administrator should consider.

---

# 17. License and OneDrive

OneDrive for Business is integrated with Microsoft 365 licensing.

Simplified:

```text
User
 ↓
Appropriate License
 ↓
OneDrive Service
 ↓
User OneDrive
```

If OneDrive is unavailable, administrators should investigate licensing as well as identity, provisioning, permissions, and service status.

---

# 18. Service Plan Troubleshooting

A user may have a Microsoft 365 license but still have a particular service disabled.

Example:

```text
User
 ↓
Microsoft 365 License
 ↓
Exchange Online → Enabled
Teams → Enabled
SharePoint → Disabled
```

In this situation, simply saying:

> "The user has a Microsoft 365 license."

is not enough.

The administrator should check the individual service plans.

---

# 19. Common Licensing Problem

### Scenario

> User cannot access Microsoft Teams.

Investigation:

```text
User
 ↓
Account Enabled?
 ↓
Correct License?
 ↓
Teams Service Plan Enabled?
 ↓
Group Membership?
 ↓
Teams Policies?
 ↓
Conditional Access?
 ↓
Device / Client?
 ↓
Service Health?
```

Licensing is only one part of the troubleshooting process.

---

# 20. Common Licensing Problem — No License Available

### Problem

```text
New Employee:
"I cannot access Microsoft 365."
```

Possible investigation:

```text
User Created
      ↓
License Assigned?
      ↓
NO
      ↓
Check Available Licenses
      ↓
Available?
   ┌───────┴───────┐
  YES             NO
   ↓               ↓
Assign         Purchase /
License        Reassign
```

---

# 21. Common Licensing Problem — Wrong License

### Scenario

A user requires functionality that is not included in their assigned plan.

Investigation:

```text
User Requirement
      ↓
Identify Required Service
      ↓
Check Current License
      ↓
Check Service Plan
      ↓
Compare Requirements
      ↓
Assign Appropriate License
```

---

# 22. License Conflict

A user may receive multiple licenses from different subscriptions.

Example:

```text
User
 │
 ├── Microsoft 365 E3
 │
 └── Additional Service License
```

This can be valid, but administrators should understand which services are provided by each license and whether there are conflicts or unnecessary assignments.

---

# 23. License Troubleshooting Checklist

When troubleshooting a licensing issue:

### User

* Is the correct user account being investigated?
* Is the account enabled?

### License

* Does the user have a license?
* Which license?
* Is the license active?

### Service Plan

* Is the required service included?
* Is the service plan enabled?

### Group

* Is the user receiving the license through a group?
* Is group membership correct?

### Subscription

* Is the subscription active?
* Are licenses available?

### Service

* Is the Microsoft service operational?

### Access

* Are permissions or policies preventing access?

---

# 24. Microsoft 365 Admin Center

Administrators can manage Microsoft 365 subscriptions and licensing through the Microsoft 365 admin center.

Depending on the admin role and interface, subscription information can be found under areas such as:

```text
Billing
   ↓
Your products / Subscriptions
```

Microsoft documentation states that subscription information can include:

* Product name
* Assigned licenses
* Total licenses
* Subscription status

---

# 25. Administrative Roles

Different administrative roles have different licensing capabilities.

Examples include:

* Global Administrator
* License Administrator
* User Administrator
* Billing Administrator

The exact permissions depend on the assigned administrative role.

For example, Microsoft documents that Global Administrators and License Administrators can assign and unassign licenses, while Billing Administrators primarily manage purchasing and billing functions.

---

# 26. PowerShell and Licensing

Microsoft 365 licensing can also be investigated using PowerShell.

Microsoft recommends the Microsoft Graph PowerShell SDK for accessing Microsoft Graph functionality.

A licensing investigation may involve:

```text
Microsoft Graph
      ↓
Subscribed SKUs
      ↓
Licensing Plans
      ↓
Service Plans
      ↓
User Assignments
```

Example command:

```powershell
Get-MgSubscribedSku
```

This can be used to retrieve subscribed SKU information when the required Microsoft Graph permissions and connection are configured.

---

# 27. Example PowerShell Workflow

A simplified workflow:

```powershell
Connect-MgGraph
```

Then:

```powershell
Get-MgSubscribedSku
```

This helps an administrator inspect available subscription SKUs.

For a real production environment, the administrator must use the appropriate permissions and follow organizational security procedures.

---

# 28. License Troubleshooting Scenario

## Incident

```text
User:
"I could use Microsoft 365 yesterday, but today I cannot access Exchange Online."
```

### Investigation

```text
1. Check User Account
        ↓
2. Check License
        ↓
3. Check Exchange Online Service Plan
        ↓
4. Check License Assignment
        ↓
5. Check Group Membership
        ↓
6. Check Account Status
        ↓
7. Check Service Health
        ↓
8. Check Exchange Online
        ↓
9. Validate
```

Possible causes:

* License removed
* License expired or subscription issue
* Exchange Online service plan disabled
* Group membership changed
* Account issue
* Service outage

---

# 29. License Troubleshooting Scenario

## Incident

```text
User:
"I have a Microsoft 365 license but I cannot install Office applications."
```

Investigation:

```text
User
 ↓
Check License
 ↓
Check Microsoft 365 Apps Service
 ↓
Check License Assignment
 ↓
Check Device
 ↓
Check Installation
 ↓
Check Activation
```

Important distinction:

```text
Cloud Service Access
        ≠
Desktop Application Installation
```

The assigned plan must include the appropriate Microsoft 365 Apps entitlement.

---

# 30. Microsoft 365 Apps Licensing

Microsoft 365 Apps uses user-based subscription licensing in supported scenarios.

Microsoft documents that a licensed user can install Microsoft 365 Apps on up to:

```text
5 PCs or Macs
5 Tablets
5 Phones
```

for plans that include that benefit.

The exact entitlement depends on the subscription.

---

# 31. Shared Computer Activation

Microsoft 365 Apps also supports **Shared Computer Activation** for appropriate scenarios.

Example:

```text
Shared Computer
       │
       ├── User A → Sign In
       ├── User B → Sign In
       └── User C → Sign In
```

Each user authenticates using their own account and appropriate license.

This is useful for environments where multiple users share the same computer.

---

# 32. Non-User Mailboxes

Not every mailbox is a normal licensed user mailbox.

Examples:

* Shared mailboxes
* Room mailboxes
* Resource mailboxes

Some non-user mailboxes can operate without an individual user license, subject to Microsoft's licensing and service limitations.

For example, Microsoft documents specific licensing requirements when shared/resource mailboxes exceed certain storage or functionality limits.

Always verify the current Microsoft licensing requirements before making a production decision.

---

# 33. License Management Best Practices

Good licensing management includes:

* Assign licenses based on business requirements.
* Use groups where appropriate for scalable assignment.
* Regularly review unused licenses.
* Remove unnecessary assignments.
* Monitor subscription status.
* Follow least-privilege principles.
* Document license changes.
* Avoid sharing user accounts.
* Review licenses during employee offboarding.
* Review licenses during department changes.

---

# 34. Joiner-Mover-Leaver and Licensing

Licensing should be part of the user lifecycle.

### Joiner

```text
Create User
    ↓
Assign License
    ↓
Enable Required Services
```

### Mover

```text
Role Changes
    ↓
Review License
    ↓
Change License if Required
    ↓
Review Services
```

### Leaver

```text
Employee Leaves
    ↓
Offboarding
    ↓
Remove / Reclaim License
    ↓
License Becomes Available
```

---

# 35. L1 Support Perspective

L1 support may:

* Check whether the user has a license.
* Identify the assigned license.
* Check basic service availability.
* Confirm the user's reported requirement.
* Check whether the account is active.
* Escalate complex licensing issues.

---

# 36. L2 Support Perspective

L2 support may investigate:

* Service plans
* Group-based licensing
* Multiple licenses
* License conflicts
* Provisioning problems
* Subscription status
* Application entitlement
* Exchange Online licensing
* Microsoft 365 Apps activation
* License-related access issues

---

# 37. Important Terminology

| Term                  | Meaning                                            |
| --------------------- | -------------------------------------------------- |
| Subscription          | Purchased Microsoft cloud offering                 |
| License               | User entitlement within a subscription             |
| Licensing Plan        | Defines available Microsoft 365 services           |
| Service Plan          | Individual service/feature within a licensing plan |
| License Assignment    | Associating a license with a user                  |
| Direct Assignment     | License assigned directly to a user                |
| Group-Based Licensing | License applied through group membership           |
| SKU                   | Product/license identifier                         |
| License Availability  | Number of unused licenses                          |
| Subscription Status   | Current state of the subscription                  |

---

# 38. Interview Questions

## Q1. What is the difference between a subscription and a license?

A subscription is the organization's purchased Microsoft service offering. A license is an entitlement from that subscription that can be assigned to a user.

---

## Q2. What is a service plan?

A service plan represents an individual Microsoft 365 service or capability included within a licensing plan.

---

## Q3. A user has a Microsoft 365 license but cannot use Teams. What do you check?

I would verify the assigned license, confirm that the Teams service plan is enabled, check group-based licensing if applicable, then investigate Teams policies, Conditional Access, device issues, and service health.

---

## Q4. What is group-based licensing?

It is a licensing approach where licenses are associated with a group and users receive the applicable license based on group membership.

---

## Q5. What happens when a user leaves the organization?

As part of the organization's offboarding process, the user's access and license should be reviewed. The license may be removed and made available for reassignment, subject to the organization's policies.

---

## Q6. Can a user have multiple licenses?

Yes. A user can have licenses from multiple licensing plans when required.

---

## Q7. Does having a license mean the user has access to everything?

No.

Licensing provides entitlement to services, while permissions, policies, group membership, application assignments, and other controls determine actual access.

---

## Q8. How can you check Microsoft 365 licensing using PowerShell?

Microsoft Graph PowerShell can be used to inspect subscription SKUs and licensing information.

Example:

```powershell
Connect-MgGraph
Get-MgSubscribedSku
```

---

# 39. Portfolio Learning Outcome

After completing this topic, I should be able to:

* Explain Microsoft 365 subscriptions.
* Explain licenses.
* Explain licensing plans.
* Explain service plans.
* Understand direct license assignment.
* Understand group-based licensing.
* Understand license availability.
* Understand license reassignment.
* Distinguish licenses from permissions.
* Understand licensing for Exchange Online.
* Understand licensing for Teams.
* Understand licensing for SharePoint and OneDrive.
* Understand Microsoft 365 Apps licensing.
* Understand shared computer activation.
* Understand licensing during Joiner-Mover-Leaver processes.
* Troubleshoot common licensing issues.
* Use Microsoft Graph PowerShell to investigate licensing.
* Explain Microsoft 365 licensing confidently in interviews.

---

# 41. Quick Revision

```text
SUBSCRIPTION
     ↓
Contains licensing plans
     ↓
LICENSE
     ↓
Assigned to user
     ↓
SERVICE PLANS
     ↓
Enable available services
     ↓
ACCESS
     ↓
Controlled by permissions + policies
```

Remember:

```text
Subscription ≠ License
License ≠ Permission
License ≠ Administrator Role
