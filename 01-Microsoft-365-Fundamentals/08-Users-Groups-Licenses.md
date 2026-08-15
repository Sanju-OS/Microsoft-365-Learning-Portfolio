# Microsoft 365 Users and Groups

## 1. Overview

Users and groups are fundamental components of a Microsoft 365 environment.

Users represent individual identities, while groups allow organizations to manage collections of users and control access to resources.

A simplified model is:

```text
Microsoft 365 Tenant
        │
        ├── Users
        │    ├── Employee A
        │    ├── Employee B
        │    └── Employee C
        │
        └── Groups
             ├── IT
             ├── HR
             ├── Finance
             └── Management
````

Users and groups are managed primarily through Microsoft Entra ID and Microsoft 365 administration tools.

---

# 2. User Account

A Microsoft 365 user account represents an identity that can access organizational resources.

A user may have:

* Display name
* User Principal Name (UPN)
* Email address
* Password/authentication methods
* License
* Group memberships
* Roles
* Application access
* Device associations

Example:

```text
User:
John Smith

UPN:
john.smith@company.com

Department:
IT

License:
Microsoft 365 License

Groups:
IT Support
All Employees
```

---

# 3. User Principal Name

UPN stands for:

**User Principal Name**

It is commonly used as the user's sign-in identity.

Example:

```text
john.smith@company.com
```

The UPN is not necessarily required to be identical to the user's primary email address, although organizations often make them the same.

---

# 4. Member Users

A member user normally represents an identity belonging to the organization.

Example:

```text
Company
   │
   ├── John
   ├── Sarah
   └── David
```

Member users can be assigned:

* Licenses
* Groups
* Applications
* Roles
* Policies

---

# 5. Guest Users

Guest users represent external identities that are invited to collaborate with an organization.

Examples:

* Contractors
* Vendors
* Partners
* Consultants
* External collaborators

Simplified:

```text
Company Tenant
      │
      ├── Internal Users
      │
      └── Guest Users
              │
              ▼
       External Organization
```

Guest access should be controlled carefully because it involves external identities.

---

# 6. User Lifecycle

A typical enterprise user lifecycle is:

```text
Joiner
   ↓
User Creation
   ↓
License Assignment
   ↓
Group Assignment
   ↓
Application Access
   ↓
Device Enrollment
   ↓
Employee Uses Services
   ↓
Mover
   ↓
Role / Department Changes
   ↓
Leaver
   ↓
Disable Access
   ↓
Remove / Reassign Resources
```

This is commonly called the **Joiner-Mover-Leaver** lifecycle.

---

# 7. Joiner Process

When a new employee joins an organization, IT may perform tasks such as:

```text
HR Request
    ↓
Create User
    ↓
Assign UPN
    ↓
Assign License
    ↓
Add Groups
    ↓
Configure MFA
    ↓
Assign Applications
    ↓
Configure Device
    ↓
Validate Access
```

The exact process depends on the organization's identity and provisioning systems.

---

# 8. Mover Process

When an employee changes department or role:

```text
Employee Changes Role
        ↓
Update User Information
        ↓
Update Groups
        ↓
Review Access
        ↓
Change Applications
        ↓
Review Licenses
        ↓
Review Device Policies
        ↓
Validate New Access
```

A mover process is important because users may otherwise retain access they no longer require.

---

# 9. Leaver Process

When an employee leaves:

```text
Employee Leaves
       ↓
Disable / Block Account
       ↓
Revoke Access
       ↓
Review Sessions
       ↓
Handle Mailbox
       ↓
Handle OneDrive
       ↓
Remove Application Access
       ↓
Recover / Reassign Resources
       ↓
Document
```

The exact offboarding process should follow organizational security and retention policies.

---

# 10. Groups

Groups allow administrators to manage multiple identities together.

Instead of configuring 100 users individually:

```text
100 Users
   ↓
Group
   ↓
Access / Policy / License
```

This makes administration more scalable.

---

# 11. Common Group Types

Important group concepts include:

* Security groups
* Microsoft 365 groups
* Distribution groups
* Dynamic groups

Each serves different purposes.

---

# 12. Security Groups

Security groups are commonly used to control access to resources.

Example:

```text
IT-Support Group
      │
 ┌────┼────┐
 │    │    │
John Sarah David
      │
      ▼
Access to Resource
```

Security groups can be used for:

* Application access
* Resource permissions
* Policy targeting
* License assignment
* Access control

---

# 13. Microsoft 365 Groups

Microsoft 365 Groups provide a collaboration-oriented membership model.

Depending on configuration and service integration, a Microsoft 365 Group can provide access to resources such as:

* Shared mailbox
* Shared calendar
* SharePoint site
* Files
* Collaboration features

Simplified:

```text
Microsoft 365 Group
        │
        ├── Members
        ├── Shared Mailbox
        ├── Calendar
        └── SharePoint Resources
```

Microsoft 365 Groups are commonly associated with collaboration scenarios.

---

# 14. Distribution Groups

Distribution groups are primarily used to distribute email to multiple recipients.

Example:

```text
support@company.com
       │
       ├── John
       ├── Sarah
       ├── David
       └── Michael
```

An email sent to the distribution group can be delivered to its members according to the group's configuration.

---

# 15. Dynamic Groups

Dynamic groups can automatically determine membership based on rules or attributes.

Example:

```text
Department = IT
        ↓
Dynamic Group
        ↓
All matching users
```

If a user's attributes change, their group membership may change automatically according to the configured rule.

This can reduce manual administration.

---

# 16. Group Ownership

Groups can have owners responsible for managing the group.

A simplified model:

```text
Group
 │
 ├── Owner
 │
 └── Members
```

Owners and members have different responsibilities and permissions depending on the group type.

---

# 17. Group Membership

A user can belong to multiple groups.

Example:

```text
John
 │
 ├── All Employees
 ├── IT
 ├── IT Support
 └── Project Alpha
```

Group membership can affect:

* Application access
* Resource access
* Licensing
* Policies
* Collaboration

---

# 18. Group-Based Licensing

Organizations can use groups to assign licenses to users.

Simplified:

```text
User
  ↓
Group Membership
  ↓
Group-Based License
  ↓
Microsoft 365 Services
```

Example:

```text
IT Employees Group
       ↓
Microsoft 365 License
       ↓
IT Users
```

This can simplify license administration for large organizations.

---

# 19. User Access Model

A user's effective access can depend on several factors.

```text
User
 │
 ├── Direct Permissions
 │
 ├── Group Membership
 │
 ├── License
 │
 ├── Application Assignment
 │
 ├── Conditional Access
 │
 └── Device Compliance
```

Therefore:

```text
User Has Account
        ≠
User Has Access to Everything
```

---

# 20. Identity vs Access

### Identity

Answers:

> Who is the user?

### Access

Answers:

> What can the user access?

Example:

```text
User
 ↓
Authentication
 ↓
Identity Confirmed
 ↓
Authorization
 ↓
Access Decision
```

---

# 21. Authentication

Authentication verifies a user's identity.

Examples:

* Password
* MFA
* Passwordless authentication
* Security keys
* Authenticator-based authentication

Simplified:

```text
User
 ↓
Credentials
 ↓
Authentication
 ↓
Identity Verified
```

---

# 22. Authorization

Authorization determines what the authenticated user can access.

Example:

```text
User
 ↓
Authenticated
 ↓
Group Membership
 ↓
Permissions
 ↓
Resource Access
```

A user can successfully authenticate but still be denied access to a resource.

---

# 23. Example — SharePoint Access

A user reports:

> "I can sign in to Microsoft 365 but cannot access the Finance SharePoint site."

Possible investigation:

```text
Authentication
      ↓
Successful
      ↓
Check SharePoint Access
      ↓
Check Group Membership
      ↓
Check Site Permissions
      ↓
Check Conditional Access
      ↓
Check Sharing Configuration
      ↓
Resolve
```

This demonstrates:

```text
Authentication ≠ Authorization
```

---

# 24. Example — Teams Access

User reports:

> "I can sign in to Microsoft 365 but cannot access a particular Team."

Investigation:

```text
User
 ↓
Authentication
 ↓
License
 ↓
Teams Membership
 ↓
Team / Channel Permissions
 ↓
Teams Policies
 ↓
Conditional Access
 ↓
Device / Client
```

The problem may not be the Teams application itself.

---

# 25. Example — Application Access

Suppose a company has an internal application called:

```text
Finance-App
```

Only Finance employees should access it.

A possible model is:

```text
Finance Users
      ↓
Finance Security Group
      ↓
Application Assignment
      ↓
Finance-App
```

When an employee joins Finance, adding them to the appropriate group can provide access.

---

# 26. User Troubleshooting Checklist

When a user reports an access problem:

### Identity

* Is the correct account being used?
* Is the UPN correct?
* Is the account enabled?

### Authentication

* Can the user authenticate?
* Is MFA working?
* Is Conditional Access affecting the sign-in?

### License

* Does the user have the required license?
* Is the required service enabled?

### Groups

* Is the user a member of the required group?
* Is group membership current?

### Permissions

* Does the user have access to the resource?
* Is access inherited through a group?

### Device

* Is the device compliant?
* Is the device registered or managed?

### Service

* Is the Microsoft service operational?

---

# 27. Example — User Cannot Access Application

### Problem

> "The application worked yesterday but not today."

Investigation:

```text
User Account
     ↓
Group Membership
     ↓
License
     ↓
Application Assignment
     ↓
Conditional Access
     ↓
Authentication
     ↓
Application Service
     ↓
Device
     ↓
Network
```

Possible root causes include:

* Group membership changed
* License removed
* Application assignment changed
* Conditional Access policy changed
* Authentication issue
* Application outage
* Device compliance problem

---

# 28. Example — User Changed Department

### Previous Department

```text
Marketing
```

### New Department

```text
IT
```

The user's access should be reviewed.

```text
Marketing Groups
       ↓
Remove obsolete access
       ↓
IT Groups
       ↓
Add required access
       ↓
Assign required applications
       ↓
Review license
       ↓
Validate
```

This is part of the **Mover** lifecycle.

---

# 29. Example — Employee Leaves

When an employee leaves:

```text
HR Notification
      ↓
Disable Account
      ↓
Revoke Access
      ↓
Review MFA / Sessions
      ↓
Handle Mailbox
      ↓
Handle OneDrive
      ↓
Remove Application Access
      ↓
Reassign Resources
      ↓
Document
```

The exact process must follow the organization's security, legal, and retention requirements.

---

# 30. Least Privilege

Users should receive only the access required for their job.

Example:

```text
Employee
   ↓
Job Role
   ↓
Required Access
   ↓
Appropriate Group
   ↓
Required Resources
```

Avoid:

```text
Employee
   ↓
Access to Everything
```

Least privilege reduces security risk.

---

# 31. Role-Based Access

Organizations can use roles and groups to structure access.

Example:

```text
IT Support
   ↓
IT Support Group
   ↓
Support Applications
   ↓
Required Permissions
```

Administrative roles should also follow least-privilege principles.

---

# 32. User and Group Troubleshooting Model

A useful support model is:

```text
                  User Issue
                      │
                      ▼
                Identify User
                      │
                      ▼
               Identify Resource
                      │
                      ▼
                Authentication
                      │
                      ▼
                Authorization
                      │
          ┌───────────┼───────────┐
          │           │           │
        License      Group      Policy
          │           │           │
          └───────────┼───────────┘
                      ▼
                  Permission
                      │
                      ▼
                   Device
                      │
                      ▼
                  Application
                      │
                      ▼
                  Resolution
```

---

# 33. Common User and Group Issues

Common incidents include:

### User Issues

* Account disabled
* Password problems
* MFA problems
* Incorrect UPN
* Missing license
* Missing application access
* Sign-in failure
* Conditional Access block

### Group Issues

* User not added
* User removed unexpectedly
* Incorrect group membership
* Group ownership issue
* Group permission issue
* Dynamic membership not updating
* Distribution group delivery problem

---

# 34. L1 Support Responsibilities

Depending on organizational permissions, L1 support may:

* Verify user identity
* Check account status
* Reset passwords
* Check basic license information
* Check group membership
* Add users to approved groups
* Troubleshoot basic access issues
* Document incidents
* Escalate complex issues

---

# 35. L2 Support Responsibilities

L2 support may investigate:

* Authentication failures
* MFA issues
* Conditional Access
* Group-based licensing
* Application access
* Dynamic groups
* Identity synchronization
* Permission problems
* Guest access
* Sign-in logs
* Root cause
* Advanced Microsoft 365 service dependencies

---

# 36. Joiner-Mover-Leaver Model

The complete lifecycle can be represented as:

```text
                 Employee Lifecycle

                       JOINER
                         │
                         ▼
                  Create Identity
                         │
                         ▼
                  Assign Access
                         │
                         ▼
                    Employee
                         │
                         ▼
                       MOVER
                         │
                         ▼
                  Change Access
                         │
                         ▼
                      LEAVER
                         │
                         ▼
                 Disable / Remove
                         │
                         ▼
                   Secure Resources
```

This model is widely applicable to enterprise IT operations.

---

# 37. Important Concepts

| Concept             | Purpose                              |
| ------------------- | ------------------------------------ |
| User                | Individual identity                  |
| UPN                 | Common sign-in identity              |
| Member              | Internal organizational identity     |
| Guest               | External collaboration identity      |
| Security Group      | Access and security management       |
| Microsoft 365 Group | Collaboration                        |
| Distribution Group  | Email distribution                   |
| Dynamic Group       | Rule-based membership                |
| Group Owner         | Manages group                        |
| Group Member        | Participates in group                |
| License             | Provides product/service entitlement |
| Authentication      | Verifies identity                    |
| Authorization       | Determines access                    |
| JML                 | Joiner-Mover-Leaver lifecycle        |

---

# 38. Interview Questions

## Q1. What is the difference between authentication and authorization?

Authentication verifies who the user is. Authorization determines what resources the authenticated user is allowed to access.

---

## Q2. What is a security group?

A security group is a collection of identities commonly used to manage access to resources, applications, policies, and other organizational capabilities.

---

## Q3. What is a Microsoft 365 Group?

A Microsoft 365 Group provides a collaboration-oriented membership model that can be associated with resources such as a shared mailbox, calendar, SharePoint site, and files.

---

## Q4. What is a distribution group?

A distribution group is primarily used to distribute email messages to multiple recipients.

---

## Q5. What is a dynamic group?

A dynamic group uses configured rules or attributes to determine membership automatically.

---

## Q6. What is a guest user?

A guest user is an external identity invited to collaborate with an organization.

---

## Q7. A user can sign in but cannot access SharePoint. What do you check?

I would distinguish authentication from authorization. I would check the user's group membership, SharePoint permissions, licensing where relevant, Conditional Access, sharing configuration, and the specific site or resource permissions.

---

## Q8. What is the Joiner-Mover-Leaver process?

It is an identity and access lifecycle model covering:

```text
Joiner → Create and provision access

Mover → Modify access when role changes

Leaver → Remove or disable access when employment ends
```

---

## Q9. Why are groups useful in enterprise environments?

Groups make access and administration scalable. Instead of managing permissions individually for every user, organizations can manage access through group membership.

---

## Q10. Why is least privilege important?

Least privilege ensures users and administrators receive only the access required for their responsibilities, reducing unnecessary security exposure.

---

# 39. Portfolio Learning Outcome

After completing this topic, I should be able to:

* Explain Microsoft 365 user accounts.
* Explain UPN.
* Understand member and guest users.
* Explain security groups.
* Explain Microsoft 365 Groups.
* Explain distribution groups.
* Explain dynamic groups.
* Understand group ownership and membership.
* Understand group-based licensing.
* Explain authentication and authorization.
* Understand the Joiner-Mover-Leaver lifecycle.
* Troubleshoot user access issues.
* Troubleshoot group membership issues.
* Understand least privilege.
* Explain users and groups during technical interviews.

---


# 41. Next Topic

The next topic is:

Microsoft 365 Licensing and Subscriptions

Topics will include:

* Microsoft 365 subscriptions
* Product licenses
* Service plans
* License assignment
* Direct licensing
* Group-based licensing
* License conflicts
* License troubleshooting
* Expired subscriptions
* Trial subscriptions
* License vs permission
* Common licensing scenarios
* L1/L2 troubleshooting
