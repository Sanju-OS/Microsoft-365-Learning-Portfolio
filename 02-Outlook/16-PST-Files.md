# Outlook PST Files

## 1. Overview

A **PST (Personal Storage Table)** is an Outlook Data File used to store Outlook information locally.

A PST can contain:

- Emails
- Calendar items
- Contacts
- Tasks
- Other Outlook data

Conceptually:

```text
Outlook
   ↓
PST File
   ↓
Local Computer Storage
````

PST files are different from the user's primary Microsoft 365 mailbox and Online Archive.

---

# 2. Why PST Files Matter in IT Support

PST-related problems can cause:

* Missing emails
* Outlook performance problems
* Outlook crashes
* PST corruption
* Import/export problems
* Missing PST files
* Duplicate emails
* Storage issues
* Access problems

For L1/L2 support, understanding PST files is important when troubleshooting legacy Outlook environments and users who maintain local archives.

---

# 3. PST vs OST

PST and OST are different Outlook data files.

| Feature                     | PST                    | OST                                                 |
| --------------------------- | ---------------------- | --------------------------------------------------- |
| Full Name                   | Personal Storage Table | Offline Storage Table                               |
| Typical Use                 | Local data/archive     | Cached mailbox data                                 |
| Local File                  | Yes                    | Yes                                                 |
| Microsoft 365 mailbox cache | No                     | Yes                                                 |
| Can be manually opened      | Yes                    | Generally not treated as a portable mailbox archive |
| Typical Use                 | Export/archive         | Offline mailbox access                              |

Simplified:

```text
PST
↓
User-managed Outlook data

OST
↓
Local cached copy of mailbox data
```

---

# 4. PST File Location

PST files are normally stored somewhere on the local computer.

The exact location can vary based on:

* Windows version
* Outlook configuration
* User configuration
* Organizational policy

Do not assume every PST exists in the same folder.

When troubleshooting, identify the actual configured file path.

---

# 5. Finding a PST File

A support engineer may need to determine which PST files are connected to Outlook.

General workflow:

```text
Outlook
   ↓
Account / Data File Settings
   ↓
Identify PST
   ↓
Check File Location
```

The exact menu names depend on the Outlook client/version.

---

# 6. Adding an Existing PST

If an authorized PST already exists, Outlook can generally open it.

Conceptually:

```text
Existing PST
     ↓
Outlook
     ↓
Open Data File
     ↓
PST Appears
```

The PST remains a local file.

---

# 7. Creating a New PST

A PST can be created when organizational policy permits local Outlook data files.

General workflow:

```text
Outlook
   ↓
Data File Management
   ↓
Add / Create Data File
   ↓
Select PST
   ↓
Choose Location
   ↓
Create
```

The exact interface depends on the Outlook version.

---

# 8. Opening a PST

General process:

```text
Open Outlook
      ↓
Open Data File
      ↓
Select PST
      ↓
Open
```

After opening, the PST may appear as an additional mailbox/data-file section in Outlook.

---

# 9. Closing a PST

Closing a PST from Outlook does **not normally delete the PST file from the computer**.

Conceptually:

```text
Close PST in Outlook
       ↓
PST Removed from Outlook View
       ↓
PST File Remains on Disk
```

This distinction is important when supporting users.

---

# 10. PST vs Archive Folder

These are different.

### Archive Folder

A folder inside the mailbox where messages may be moved.

### PST

A separate local data file.

Example:

```text
Archive Folder
    ↓
Mailbox

PST
    ↓
Local Computer
```

Do not describe a PST as the same thing as Microsoft 365 Online Archive.

---

# 11. Exporting Outlook Data to PST

Outlook may provide an export mechanism for supported mailbox data.

Conceptually:

```text
Mailbox
   ↓
Export
   ↓
PST
   ↓
Local Storage
```

Exporting company email to PST should follow organizational policy.

---

# 12. Importing PST Data

A PST can also be imported into Outlook.

Conceptually:

```text
PST
 ↓
Import
 ↓
Outlook
 ↓
Mailbox / Folder
```

Before importing, verify:

* Source PST
* Destination
* Required permissions
* Data ownership
* Organizational policy
* Duplicate handling

---

# 13. PST Backup Considerations

A PST is a local file.

Therefore, it can be affected by:

* Disk failure
* Accidental deletion
* File corruption
* Device replacement
* Malware
* Unauthorized copying

A PST should not automatically be treated as a secure enterprise backup.

---

# 14. PST and Microsoft 365

Microsoft 365 mailbox data is normally stored in Exchange Online.

A PST is local.

Conceptually:

```text
Microsoft 365
     ↓
Exchange Online
     ↓
Cloud Mailbox
```

versus:

```text
PST
 ↓
Local Storage
```

The two should not be confused.

---

# 15. PST and Outlook Performance

Large PST files can contribute to Outlook performance problems, depending on the Outlook version, storage conditions, and overall configuration.

Symptoms may include:

* Slow Outlook
* Delayed folder loading
* Slow searching
* Application hangs
* Long startup times

If a user reports Outlook performance problems, identify whether large local data files are involved.

Related documentation:

[Outlook Performance](./22-Outlook-Performance.md)

---

# 16. Large PST Files

A large PST can increase troubleshooting complexity.

Possible symptoms:

```text
Outlook
   ↓
Large PST
   ↓
Longer processing
   ↓
Performance problems
```

Do not immediately delete or split a PST.

First determine:

* File size
* Importance of data
* Whether the data exists elsewhere
* Whether the PST is actively being used
* Organizational policy

---

# 17. PST Corruption

A PST can become corrupted.

Possible symptoms:

* Outlook reports data-file errors
* PST cannot be opened
* Folders disappear
* Messages cannot be accessed
* Outlook becomes unstable when accessing the PST
* Error messages appear when opening the file

Simplified:

```text
PST
 ↓
Corruption
 ↓
Access / Performance Problems
```

---

# 18. PST Corruption Troubleshooting

Initial workflow:

```text
User Reports PST Problem
          ↓
Confirm PST Location
          ↓
Check File Accessibility
          ↓
Check Whether Backup Exists
          ↓
Close PST in Outlook
          ↓
Use Approved Repair Procedure
          ↓
Test PST
```

Always follow organizational support procedures before attempting repair.

---

# 19. Outlook Inbox Repair Tool

Microsoft provides an Inbox Repair Tool (`SCANPST.EXE`) for repairing certain Outlook data-file problems.

Conceptually:

```text
Corrupted PST
      ↓
SCANPST
      ↓
Analyze
      ↓
Repair
      ↓
Validate
```

The tool and its location can vary depending on the Outlook installation.

Do not assume that every PST corruption issue can be repaired successfully.

---

# 20. Before Repairing a PST

Before attempting repair:

```text
[ ] Identify correct PST
[ ] Confirm user owns/uses the file
[ ] Confirm file path
[ ] Check whether backup exists
[ ] Close Outlook if required
[ ] Preserve original data where appropriate
[ ] Follow company procedure
```

A repair attempt should not unnecessarily put the only copy of important data at risk.

---

# 21. PST File Cannot Be Found

### User Report

> "My old PST was connected yesterday, but now it is missing."

Troubleshooting:

```text
Check Outlook Data Files
        ↓
Identify Expected Path
        ↓
Check File System
        ↓
Search Approved Locations
        ↓
Check Network / External Storage if Applicable
        ↓
Check Backup
```

Possible causes include:

* File moved
* File renamed
* File deleted
* Drive unavailable
* Network location unavailable
* User changed computer

---

# 22. PST File Moved

If a PST was moved after being configured in Outlook, Outlook may report that the file cannot be found.

Conceptually:

```text
Outlook
   ↓
Expected PST Path
   ↓
File Not Found
```

Correct the configured path only after confirming the correct PST file.

Do not connect an unrelated PST just because the filename looks similar.

---

# 23. PST File Renamed

Example:

```text
Old:
Archive.pst

New:
Archive-2026.pst
```

Outlook may continue expecting the original path/name.

Verify the actual file before reconnecting it.

---

# 24. PST Stored on Network Location

PST files stored on network shares can introduce additional risks and performance issues.

Potential factors include:

* Network connectivity
* File locking
* Latency
* Permissions
* Availability

Organizations should define whether network-based PST usage is permitted.

Do not recommend moving PST files to network storage without checking company policy.

---

# 25. PST on External Drive

A PST stored on an external drive may become unavailable when the drive is disconnected.

Example:

```text
External Drive
      ↓
PST
      ↓
Disconnect Drive
      ↓
Outlook Cannot Access PST
```

Check:

* Drive connection
* Drive letter
* File path
* Permissions
* File integrity

---

# 26. PST Permission Problem

A user may have a PST but lack sufficient access to the file.

Check:

```text
PST File
   ↓
Windows File Permissions
   ↓
User Access
```

Possible symptoms:

* Cannot open PST
* Access denied
* Read/write errors

Follow the organization's endpoint and file-permission procedures.

---

# 27. PST Password

PST files may be configured with a password.

If the user cannot open a password-protected PST:

```text
PST
 ↓
Password Prompt
 ↓
Valid Password?
```

Do not attempt to bypass security controls.

If the password is unavailable, follow the organization's approved recovery process.

---

# 28. PST and Duplicate Emails

Importing a PST can sometimes result in duplicate content depending on the import method and destination.

Before importing:

```text
Identify Source
      ↓
Identify Destination
      ↓
Check Existing Data
      ↓
Choose Appropriate Import Method
      ↓
Validate
```

Avoid importing the same PST repeatedly without understanding the consequences.

---

# 29. PST Export Scenario

### User Requirement

> "I need a copy of my old emails."

Possible workflow:

```text
Identify Required Data
       ↓
Confirm Authorization
       ↓
Export
       ↓
PST
       ↓
Secure Storage
```

Before export, verify whether the organization permits local copies of company data.

---

# 30. PST Import Scenario

### User Requirement

> "I received my old PST and need the emails in Outlook."

Workflow:

```text
Validate PST Source
       ↓
Scan / Verify File
       ↓
Open or Import
       ↓
Select Destination
       ↓
Check Duplicates
       ↓
Validate Messages
```

Do not import unknown PST files into a corporate environment without appropriate authorization.

---

# 31. PST and Security

PST files can contain sensitive business information.

Examples:

* Customer emails
* Employee information
* Contracts
* Financial information
* Internal communications

Therefore:

```text
PST
 ↓
Sensitive Data
 ↓
Protect File
```

Avoid storing corporate PST files in:

* Personal cloud storage
* Personal email
* Unapproved USB devices
* Personal computers

unless explicitly authorized by organizational policy.

---

# 32. PST and Data Loss

A PST is not automatically protected like a centrally managed Microsoft 365 mailbox.

Possible risks:

```text
PST
 ↓
Laptop Failure
 ↓
Data Loss
```

or:

```text
PST
 ↓
Accidental Deletion
 ↓
Data Loss
```

Enterprise policies should determine whether PST usage is permitted.

---

# 33. PST Troubleshooting Decision Tree

```text
                    PST Issue
                       ↓
              Can Outlook See PST?
                 /           \
               Yes            No
                ↓              ↓
        Can PST Open?     Check File Path
          /      \             ↓
        Yes       No       Check File Exists
         ↓         ↓            ↓
    Check Data   Check       Check Permissions
                Corruption       ↓
                    ↓        Check Storage
                Repair if         ↓
                Appropriate     Reconnect
```

---

# 34. Scenario — PST Will Not Open

### User Report

> "Outlook says the data file cannot be opened."

Investigation:

```text
Confirm PST Path
       ↓
Check File Exists
       ↓
Check File Permissions
       ↓
Check File Size
       ↓
Check Whether Another Application Uses It
       ↓
Check for Corruption
```

If corruption is suspected, follow the organization's approved PST repair process.

---

# 35. Scenario — Outlook Becomes Slow After Adding PST

### User Report

> "Outlook became very slow after I added an old PST."

Investigation:

```text
Check PST Size
      ↓
Check Number of Data Files
      ↓
Check Disk Performance
      ↓
Check Search/Indexing
      ↓
Check Outlook Performance
```

Do not assume the PST is automatically the root cause.

Use controlled troubleshooting to establish correlation.

---

# 36. Scenario — PST Missing After Computer Replacement

### User Report

> "My old emails were stored in a PST, but I got a new laptop."

Investigation:

```text
New Computer
      ↓
Is PST Available?
      ↓
No
      ↓
Check Approved Backup
      ↓
Check Old Device
      ↓
Check Organization Storage
```

If no copy exists, escalate according to the organization's data recovery process.

---

# 37. Scenario — User Accidentally Deleted PST

### Incident

> "I deleted my PST."

Do not immediately create a new PST.

First:

```text
Stop Further Changes
       ↓
Check Recycle Bin
       ↓
Check Approved Backup
       ↓
Check Device Recovery Options
       ↓
Escalate if Necessary
```

If the PST contained important business data, follow the organization's data recovery process.

---

# 38. L1 Support Checklist

```text
[ ] Confirm user
[ ] Identify PST filename
[ ] Identify file path
[ ] Check whether file exists
[ ] Check whether Outlook detects it
[ ] Check permissions
[ ] Check storage location
[ ] Check file accessibility
[ ] Check for known backup
[ ] Document findings
```

---

# 39. L2 Support Checklist

```text
[ ] Determine PST size
[ ] Determine PST location
[ ] Check corruption symptoms
[ ] Check Outlook profile
[ ] Check indexing
[ ] Check performance impact
[ ] Review network/external storage
[ ] Review security policy
[ ] Use approved repair tools
[ ] Validate repaired PST
[ ] Document root cause
```

---

# 40. PST Support Ticket Example

```text
Issue:
User unable to open an existing PST file.

Symptoms:
Outlook reports that the data file cannot be opened.

Investigation:
Verified PST path.
Confirmed file exists.
Checked user permissions.
Compared file accessibility outside Outlook.
Investigated potential data-file corruption.

Action:
Followed approved PST repair procedure.

Validation:
PST successfully opened in Outlook.
User confirmed required folders and messages were accessible.

Status:
Resolved.
```

---

# 41. PST Best Practices

### Do

* Follow organizational PST policy
* Protect PST files
* Verify file paths
* Keep approved backups where required
* Validate files before importing
* Document PST-related incidents
* Use approved repair procedures

### Don't

* Delete a PST without authorization
* Move company PSTs to personal storage
* Assume PST is a backup
* Import unknown PST files
* Store sensitive company data on unauthorized devices
* Repeatedly import the same PST without checking duplicates
* Attempt to bypass PST passwords

---

# 42. Key Takeaways

* PST is a local Outlook data file.
* PST and OST serve different purposes.
* PST is different from Microsoft 365 Online Archive.
* PST files can contain important business data.
* PST corruption can cause access and performance problems.
* Large PSTs can contribute to Outlook performance issues.
* `SCANPST.EXE` can repair certain Outlook data-file problems.
* Always verify the PST file path before reconnecting it.
* Corporate PST files should be handled according to organizational security and data-management policies.
* A PST should not automatically be considered an enterprise backup.

---

## Related Documentation

* [Outlook Overview](./01-Outlook-Overview.md)
* [Outlook Configuration](./02-Outlook-Configuration.md)
* [Outlook Profile](./04-Outlook-Profile.md)
* [Outlook Profile Corruption](./06-Outlook-Profile-Corruption.md)
* [Email Management](./07-Email-Management.md)
* [Search](./14-Search.md)
* [Archive](./15-Archive.md)
* [Outlook Performance](./22-Outlook-Performance.md)
* [Outlook Crash Issues](./24-Outlook-Crash-Issues.md)
* [Real-World Scenarios](./25-Real-World-Scenarios.md)
