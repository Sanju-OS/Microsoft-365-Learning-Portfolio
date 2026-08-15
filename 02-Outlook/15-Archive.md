# Outlook Archive

## 1. Overview

Outlook provides several ways to move older email out of the user's primary mailbox view.

In a Microsoft 365 environment, it is important to distinguish between:

- Online Archive
- Manual Archive
- AutoArchive
- PST-based archiving
- Retention policies

These mechanisms are **not interchangeable**.

A simplified concept is:

```text
User Mailbox
     ↓
Email
     ↓
Archive Method
     ↓
Archive Location
````

---

# 2. Why Archiving Is Used

Organizations may use archiving to:

* Organize older messages
* Reduce clutter in the primary mailbox
* Improve mailbox management
* Retain business records according to policy
* Provide users access to historical messages

Archiving requirements should always follow the organization's retention and compliance policies.

---

# 3. Online Archive

Microsoft 365 can provide an **Online Archive mailbox** for eligible users.

Conceptually:

```text
Primary Mailbox
       +
Online Archive
       ↓
User's Microsoft 365 Mailbox
```

The Online Archive is separate from the user's primary mailbox.

It is stored in Microsoft 365 rather than as a local PST file.

---

# 4. Primary Mailbox vs Online Archive

### Primary Mailbox

Used for normal day-to-day email.

```text
Inbox
Sent Items
Deleted Items
Drafts
Other folders
```

### Online Archive

Used for archived mailbox content.

```text
Online Archive
 ├── Inbox
 ├── Sent Items
 └── Other archived folders
```

The exact folder structure depends on how items are archived.

---

# 5. Online Archive vs PST

These are different.

| Feature                | Online Archive       | PST                       |
| ---------------------- | -------------------- | ------------------------- |
| Storage                | Microsoft 365        | Local file                |
| Cloud-based            | Yes                  | No                        |
| Central administration | Yes                  | Limited                   |
| User can move items    | Yes, where permitted | Yes                       |
| Device dependency      | Lower                | Higher                    |
| Backup concerns        | Organization-managed | File-management dependent |

A PST is a local Outlook Data File.

See:

[PST Files](./16-PST-Files.md)

---

# 6. Manual Archiving

A user may manually move an email or folder into an archive location.

Conceptually:

```text
Email
 ↓
Select
 ↓
Archive / Move
 ↓
Archive Location
```

The exact options vary by Outlook version and configuration.

---

# 7. Archive Button vs Online Archive

These concepts can be confused.

The **Archive** action may move an item to an Archive folder in the mailbox.

The **Online Archive** is a separate archive mailbox.

Therefore:

```text
Archive Button
      ≠
Online Archive
```

Always identify which archive mechanism the user is referring to.

---

# 8. AutoArchive

AutoArchive is an Outlook feature that can automatically move older items according to configured settings.

Conceptually:

```text
Email Age
   ↓
AutoArchive Rule
   ↓
Older Than Configured Period
   ↓
Archive Location
```

AutoArchive behavior depends on the Outlook version and configuration.

---

# 9. AutoArchive vs Microsoft 365 Retention

These are not the same.

### AutoArchive

Primarily an Outlook client-side archiving mechanism.

### Microsoft 365 Retention

An organization-level information governance capability.

Simplified:

```text
AutoArchive
→ Outlook organization of older mail

Retention
→ Organization-defined information lifecycle
```

Do not use AutoArchive as a substitute for a compliance retention policy.

---

# 10. Retention Policies

Microsoft 365 organizations may configure retention policies to manage how long content is retained and what happens to it.

Retention can involve:

* Email
* SharePoint content
* OneDrive content
* Teams content
* Other Microsoft 365 data

Retention requirements are organization-specific.

Support engineers should follow documented policies rather than changing retention settings independently.

---

# 11. Retention vs Archive

These are different concepts.

### Archive

Changes where an item is stored or organized.

### Retention

Controls how long content should be retained and how it should be managed according to policy.

Example:

```text
Archive
Email
  ↓
Move to archive location
```

versus:

```text
Retention
Email
  ↓
Retention policy
  ↓
Lifecycle action
```

---

# 12. Online Archive Enablement

An administrator may enable Online Archive for an eligible mailbox.

Conceptually:

```text
Administrator
     ↓
Identify User
     ↓
Verify Licensing / Eligibility
     ↓
Enable Archive
     ↓
Exchange Online
     ↓
Online Archive Available
```

Exact administrative steps depend on the Microsoft 365 / Exchange Online configuration.

---

# 13. Online Archive Visibility

After Online Archive is enabled, the archive may appear in Outlook as a separate mailbox or archive area.

Example:

```text
User Mailbox
 ├── Inbox
 ├── Sent Items
 └── Deleted Items

Online Archive
 ├── Inbox
 ├── Sent Items
 └── Other folders
```

Availability and presentation can vary between Outlook clients.

---

# 14. Online Archive Not Appearing

### User Report

> "My Online Archive is missing."

Troubleshooting:

```text
Check Account
     ↓
Check Archive Enablement
     ↓
Check Outlook Web
     ↓
Check Outlook Desktop
     ↓
Check License / Eligibility
     ↓
Check Synchronization
```

Do not immediately recreate the Outlook profile.

---

# 15. Archive Works on Web but Not Desktop

Example:

```text
Outlook Web
     ↓
Online Archive Visible

Outlook Desktop
     ↓
Archive Missing
```

This suggests investigating:

* Outlook Desktop
* Profile
* Client configuration
* Synchronization
* Cached mailbox state

The server-side archive may already be functioning correctly.

---

# 16. Archive Missing on Both Web and Desktop

Example:

```text
Outlook Web     → Missing
Outlook Desktop → Missing
```

Investigate:

* Mailbox configuration
* Archive enablement
* Licensing/eligibility
* Organizational configuration
* Service-side status

This is different from a desktop-only problem.

---

# 17. Email Automatically Moved to Archive

### User Report

> "My old emails disappeared from my Inbox."

Do not immediately assume deletion.

Check:

```text
Inbox
 ↓
Archive Folder
 ↓
Online Archive
 ↓
Deleted Items
```

Also investigate:

* Rules
* Retention
* AutoArchive
* User actions

---

# 18. Email Missing After Archiving

Use this workflow:

```text
Identify Email
      ↓
Search Primary Mailbox
      ↓
Search Online Archive
      ↓
Check Archive Folder
      ↓
Check Deleted Items
      ↓
Check Other Folders
      ↓
Investigate Retention
```

Collect:

* Sender
* Subject
* Approximate date
* Recipient
* Expected location

---

# 19. Search the Online Archive

If a user says:

> "I can't find my old email."

Search both:

```text
Primary Mailbox
        +
Online Archive
```

The search scope is important.

An email may exist in the archive but not in the primary mailbox.

Related documentation:

[Search](./14-Search.md)

---

# 20. Archive Folder vs Online Archive

This distinction is extremely important for support.

### Archive Folder

A folder within the mailbox where messages can be moved.

### Online Archive

A separate archive mailbox.

Conceptually:

```text
Primary Mailbox
 └── Archive Folder

Online Archive
 └── Archived Mail
```

Do not tell a user that these are automatically the same thing.

---

# 21. User Accidentally Archived an Email

### Incident

> "I accidentally clicked Archive and my email disappeared."

First locate the message.

Possible location:

```text
Archive Folder
```

Search using:

```text
Sender
Subject
Date
Keyword
```

If found, the message can be moved back to the desired folder according to the user's requirement.

---

# 22. Archive Button Behavior

The Archive action can move a selected message out of the Inbox.

Example:

```text
Inbox
 ↓
Select Message
 ↓
Archive
 ↓
Archive Folder
```

The exact behavior and destination can vary by Outlook experience and configuration.

---

# 23. Archive and Mailbox Size

Archiving may help organize mailbox content, but it should not automatically be described as a universal solution for mailbox storage problems.

Mailbox size management depends on:

* Primary mailbox quota
* Online Archive
* Retention configuration
* Licensing
* Organization policy
* PST usage

Always identify the actual storage problem first.

---

# 24. Archive Policy

Organizations may have policies controlling how older mail is handled.

Example concept:

```text
Email Age
    ↓
Policy Evaluation
    ↓
Action
    ↓
Archive / Retain / Other Policy Action
```

The actual policy depends on the organization's Microsoft 365 configuration.

---

# 25. Archive Troubleshooting Layers

When troubleshooting an archive issue, think in layers:

```text
Layer 1
User Action

Layer 2
Outlook Client

Layer 3
Mailbox

Layer 4
Online Archive

Layer 5
Exchange Online

Layer 6
Retention / Compliance

Layer 7
Licensing / Organization Configuration
```

This prevents unnecessary client-side changes.

---

# 26. Scenario — User Cannot Find Old Email

### Incident

> "An email from two years ago is missing."

### Investigation

```text
Search Primary Mailbox
       ↓
Search Online Archive
       ↓
Check Archive Folder
       ↓
Check Deleted Items
       ↓
Check Retention / Lifecycle
```

### Important

Do not tell the user that the email was deleted until its actual location and applicable retention behavior have been investigated.

---

# 27. Scenario — Online Archive Missing

### Incident

> "I used to have an Online Archive, but it disappeared."

### Investigation

```text
Check Outlook Web
        ↓
Archive Visible?
        ↓
Yes → Desktop Client Investigation

No
 ↓
Check Mailbox Configuration
 ↓
Check Eligibility / Licensing
 ↓
Check Organization Configuration
```

### Validation

Confirm the archive is visible and accessible from the intended Outlook clients.

---

# 28. Scenario — Old Emails Automatically Moved

### Incident

> "Older emails keep moving out of my Inbox."

Possible areas to investigate:

```text
Rules
 ↓
AutoArchive
 ↓
Retention / Lifecycle
 ↓
Manual User Actions
```

Identify the actual mechanism before changing settings.

---

# 29. Scenario — Archive Works on One Device

Example:

```text
Laptop
 ↓
Online Archive Visible

Desktop
 ↓
Online Archive Missing
```

Because the archive works elsewhere, investigate the affected Outlook client before making mailbox-level changes.

---

# 30. Archive and Compliance

Archiving and compliance should not be treated as identical.

An organization may have legal, regulatory, or business requirements governing retention.

Examples of considerations:

* Retention periods
* Legal hold
* Data governance
* Information protection
* Audit requirements

Support engineers should follow organizational procedures when dealing with these areas.

---

# 31. Legal Hold / Compliance Considerations

If an organization has placed content under a legal or compliance hold, support engineers should **not manually delete or alter content** simply because a user requests it.

Escalate according to organizational procedures.

```text
User Request
    ↓
Compliance / Retention Consideration
    ↓
Follow Organization Policy
```

---

# 32. PST-Based Archiving

PST files can be used to store Outlook data locally.

Conceptually:

```text
Outlook
   ↓
PST File
   ↓
Local Storage
```

PST management has additional risks:

* File corruption
* Data loss
* Duplicate copies
* Difficult backup management
* Unauthorized storage
* Device dependency

Related documentation:

[PST Files](./16-PST-Files.md)

---

# 33. Online Archive vs PST

```text
Online Archive
      ↓
Microsoft 365
      ↓
Organization-managed

PST
      ↓
Local File
      ↓
User / Device-managed
```

For enterprise environments, follow organizational policy before creating or using PST files.

---

# 34. Archive Security

Archived emails may contain sensitive company information.

Consider:

* Access permissions
* Data protection
* Device security
* Organizational retention requirements
* Unauthorized PST exports

Do not move company email into personal storage without authorization.

---

# 35. L1 Support Checklist

```text
[ ] Confirm user
[ ] Identify missing email
[ ] Identify approximate date
[ ] Search Inbox
[ ] Search Archive folder
[ ] Search Online Archive
[ ] Check Deleted Items
[ ] Check Outlook Web
[ ] Check rules
[ ] Check user actions
[ ] Document findings
```

---

# 36. L2 Support Checklist

```text
[ ] Determine scope
[ ] Compare Desktop vs Web
[ ] Verify Online Archive status
[ ] Verify mailbox configuration
[ ] Verify eligibility / licensing
[ ] Investigate retention behavior
[ ] Investigate AutoArchive where applicable
[ ] Investigate PST usage
[ ] Check service health
[ ] Escalate compliance issues
[ ] Validate remediation
[ ] Document root cause
```

---

# 37. Archive Troubleshooting Decision Tree

```text
                  Archive Issue
                       ↓
              What Does User Mean?
                 /            \
        Archive Button       Online Archive
             ↓                     ↓
      Check Archive Folder   Check Web
             ↓                     ↓
        Search Item          Check Enablement
                                   ↓
                           Check Eligibility
                                   ↓
                           Check Configuration
                                   ↓
                              Check Client
                                   ↓
                                  Test
```

---

# 38. Support Ticket Example

```text
Issue:
User unable to locate older email.

Investigation:
Searched primary mailbox, Archive folder and Online Archive.

Finding:
Email was located in Online Archive.

Action:
Explained archive location and verified access.

Validation:
User successfully opened the archived message.

Status:
Resolved.
```

---

# 39. Best Practices

### Do

* Understand which archive mechanism is involved
* Search both primary mailbox and Online Archive
* Compare Outlook Desktop and Web
* Check policies before changing retention behavior
* Follow compliance procedures
* Document the actual location of missing email

### Don't

* Treat Archive and Online Archive as identical
* Assume archived email is deleted
* Delete archived content without authorization
* Disable retention policies to solve a user issue
* Create PST files without considering company policy
* Change compliance settings without authorization

---

# 40. Key Takeaways

* Microsoft 365 supports Online Archive functionality for eligible mailboxes.
* The Archive folder and Online Archive are different concepts.
* PST files are different from Online Archive.
* AutoArchive and Microsoft 365 retention are not the same.
* Missing old emails should be searched across multiple locations.
* Outlook Web is useful for isolating client-side archive problems.
* Retention and compliance settings require careful handling.
* Support engineers should identify the actual archive mechanism before troubleshooting.

---

## Related Documentation

* [Outlook Overview](./01-Outlook-Overview.md)
* [Outlook Configuration](./02-Outlook-Configuration.md)
* [Outlook Profile](./04-Outlook-Profile.md)
* [Email Management](./07-Email-Management.md)
* [Rules](./08-Rules.md)
* [Calendar](./11-Calendar.md)
* [Categories](./13-Categories.md)
* [Search](./14-Search.md)
* [PST Files](./16-PST-Files.md)
* [Shared Mailbox](./17-Shared-Mailbox.md)
* [Autodiscover](./19-Autodiscover.md)
* [Mail Send/Receive Issues](./23-Mail-Send-Receive-Issues.md)
* [Real-World Scenarios](./25-Real-World-Scenarios.md)
