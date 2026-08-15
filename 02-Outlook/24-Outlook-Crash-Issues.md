# Outlook Crash Issues

## 1. Overview

An Outlook crash occurs when the application unexpectedly closes, becomes unresponsive, or terminates while the user is performing an operation.

Common examples:

- Outlook closes immediately after opening
- Outlook crashes while sending email
- Outlook crashes when opening an attachment
- Outlook crashes when searching
- Outlook crashes when opening Calendar
- Outlook crashes when accessing a shared mailbox
- Outlook repeatedly crashes after startup
- Outlook displays "Not Responding" and then closes
- Outlook crashes after an Office or Windows update

A crash can originate from several layers:

```text
User
 ↓
Windows
 ↓
Outlook
 ↓
Add-ins
 ↓
Outlook Profile
 ↓
OST / Local Data
 ↓
Office Installation
 ↓
Network / Microsoft 365
````

---

# 2. Common Crash Symptoms

Users may report:

* Outlook suddenly closes
* Outlook freezes
* Outlook becomes "Not Responding"
* Outlook restarts unexpectedly
* Outlook crashes during startup
* Outlook crashes when performing a specific action
* Outlook crashes repeatedly
* Outlook crashes only on one computer
* Outlook crashes after enabling an add-in
* Outlook crashes after an update

---

# 3. First Troubleshooting Questions

Ask:

1. When did the crashing begin?
2. Does Outlook crash immediately after opening?
3. What action causes the crash?
4. Does it happen every time?
5. Is it affecting only one user?
6. Does Outlook Web work?
7. Does Outlook Safe Mode work?
8. Did Office recently update?
9. Did Windows recently update?
10. Were any add-ins installed or updated?
11. Does another Windows user experience the same issue?
12. Does the same user experience the issue on another computer?

---

# 4. Determine the Pattern

Identify whether the crash is:

```text
Startup Crash
Action-Specific Crash
Intermittent Crash
Continuous Crash
System-Wide Crash
```

The pattern is often more useful than the error message alone.

---

# 5. Startup Crash

Example:

```text
Open Outlook
    ↓
Loading Profile
    ↓
Crash
```

Possible areas:

* Outlook profile
* Add-ins
* OST/cache
* Office installation
* Authentication
* Windows components

Start with Safe Mode testing.

---

# 6. Action-Specific Crash

Example:

```text
Outlook Opens Normally
        ↓
Open Calendar
        ↓
Crash
```

or:

```text
Outlook Opens Normally
        ↓
Open Attachment
        ↓
Crash
```

This narrows the investigation.

Possible causes may include:

* Add-in
* Specific message
* Attachment integration
* Calendar integration
* Corrupted local data

---

# 7. Intermittent Crash

Example:

```text
Outlook
 ↓
Works
 ↓
Crash
 ↓
Works
 ↓
Crash
```

Record:

* Time of crash
* User action
* Network condition
* Application state
* Other applications running
* Error message

Patterns can reveal the cause.

---

# 8. Check Whether Outlook Web Works

Test:

```text
Outlook Web
      ↓
Works?
```

If Outlook Web works but desktop Outlook crashes:

```text
Mailbox / Service
       ↓
Likely Working

Desktop Client
       ↓
Investigate
```

Focus on:

* Outlook
* Profile
* Add-ins
* Office installation
* Windows

---

# 9. Outlook Safe Mode

Safe Mode is an important diagnostic test.

Conceptually:

```text
Normal Outlook
      ↓
Crashes

Safe Mode
      ↓
Works?
```

If Outlook works correctly in Safe Mode, investigate add-ins and other startup components.

If it still crashes, continue investigating other layers.

---

# 10. Safe Mode Decision

```text
          Outlook Crash
               ↓
          Test Safe Mode
           /          \
        Works         Crashes
          ↓              ↓
      Add-ins /       Profile /
      Startup         Office /
      Components      Windows
```

Safe Mode is a **diagnostic isolation technique**, not necessarily the final solution.

---

# 11. Add-ins

Outlook add-ins can sometimes contribute to:

* Crashes
* Freezing
* Slow startup
* High CPU
* Application instability

Examples:

* Meeting add-ins
* CRM integrations
* Security integrations
* Document-management integrations
* Productivity tools

---

# 12. Add-in Isolation

Test:

```text
Normal Outlook
 ↓
Crash

Safe Mode
 ↓
No Crash
```

Then investigate:

```text
Installed Add-ins
       ↓
Disable approved non-essential add-in
       ↓
Restart Outlook
       ↓
Test
```

If the crash disappears, the add-in becomes a strong suspect.

---

# 13. Re-enable Add-ins Systematically

Do not enable everything at once.

Use:

```text
Add-in A → Test
Add-in B → Test
Add-in C → Test
```

This helps identify which component is associated with the crash.

---

# 14. Outlook Profile

A damaged Outlook profile can cause:

* Startup crashes
* Synchronization problems
* Connection problems
* Application instability

Test:

```text
Existing Profile
      ↓
Crash

New Profile
      ↓
Works?
```

If the new profile works, the original profile may be involved.

---

# 15. Profile Troubleshooting

Before creating a new profile:

1. Confirm the issue.
2. Test Outlook Web.
3. Test Safe Mode.
4. Check add-ins.
5. Check Windows resources.
6. Capture relevant errors.
7. Create a new profile if appropriate.

Avoid using profile recreation as the first response to every Outlook problem.

---

# 16. OST / Cached Data

Outlook may use local cached mailbox data.

Simplified:

```text
Exchange Online
      ↓
Mailbox
      ↓
Local Cache
      ↓
Outlook
```

Problems with local cached data can contribute to:

* Crashes
* Synchronization issues
* Search issues
* Performance problems

Follow approved procedures before rebuilding or removing local Outlook data.

---

# 17. Office Installation

Outlook is part of Microsoft 365 Apps / Microsoft Office.

If Outlook repeatedly crashes, investigate the Office installation.

Possible remediation options may include:

* Office update
* Quick Repair
* Online Repair

Use the organization's approved repair procedure.

---

# 18. Office Update

Determine whether the crash started after an Office update.

Example:

```text
Before Update
 ↓
Outlook Normal

After Update
 ↓
Outlook Crashes
```

Collect:

* Office version
* Build number
* Update date
* Crash frequency
* Affected users
* Affected devices

Check organizational guidance and known issues before making changes.

---

# 19. Windows Update

A Windows update can sometimes affect application behavior.

Example:

```text
Windows Update
      ↓
Outlook Behavior Changed
```

Determine whether:

* Outlook alone is affected
* Other Office applications are affected
* The entire computer is unstable
* Other users have the same problem

---

# 20. Event Viewer

Windows Event Viewer can provide useful crash information.

Conceptually:

```text
Outlook Crash
      ↓
Windows Event Logs
      ↓
Application Error
      ↓
Faulting Application
      ↓
Faulting Module
```

Look for relevant events around the exact crash time.

---

# 21. Useful Crash Information

Capture information such as:

* Faulting application
* Application version
* Faulting module
* Exception code
* Fault offset
* Timestamp

Do not assume the faulting module is automatically the root cause. It is evidence that needs interpretation.

---

# 22. Crash Timing

Compare:

```text
User Action
      ↓
Timestamp
      ↓
Crash Event
```

Example:

```text
10:15:32
User opens attachment

10:15:35
Outlook crashes

10:15:36
Application Error recorded
```

Matching timestamps can help correlate the user report with system evidence.

---

# 23. Windows Reliability Monitor

Windows Reliability Monitor can help identify application failures over time.

It can provide a timeline showing:

```text
Date
 ↓
Application Failure
 ↓
Outlook
 ↓
Windows / Application Events
```

This can be useful when crashes are intermittent.

---

# 24. Crash Frequency

Document how often the crash occurs:

```text
Every startup
Every 10 minutes
Once per day
Only with attachments
Only with Calendar
Only when searching
```

Example:

```text
Crash occurs every time Calendar is opened.
```

This is much more useful than simply recording:

> "Outlook crashes."

---

# 25. Outlook Crashes When Opening Attachment

Possible areas:

* Attachment type
* Office application
* Security software
* Add-in
* File previewer
* Local Office installation

Test:

```text
Attachment A
 ↓
Crash

Attachment B
 ↓
Works
```

If only one file causes the crash, investigate that file separately.

---

# 26. Outlook Crashes During Search

If:

```text
Normal Outlook
 ↓
Works

Search
 ↓
Crash
```

Investigate:

* Search/indexing
* Local Outlook data
* Profile
* Office installation
* Specific search query/data

Do not immediately assume Microsoft 365 is unavailable.

---

# 27. Outlook Crashes When Opening Calendar

Possible areas:

* Calendar data
* Add-ins
* Profile
* Cached data
* Office installation

Test:

```text
Outlook Web Calendar
       ↓
Works?

Desktop Calendar
       ↓
Crashes?
```

If Web works but Desktop crashes, focus on the client.

---

# 28. Outlook Crashes With Shared Mailbox

If the crash started after adding a shared mailbox:

```text
Before Shared Mailbox
 ↓
Normal

After Shared Mailbox
 ↓
Crash
```

Investigate:

* Shared mailbox size
* Folder synchronization
* Automapping
* Permissions
* Outlook profile
* Cached data

See:

[Shared Mailbox](./17-Shared-Mailbox.md)

---

# 29. Outlook Crashes Only for One User

Example:

```text
User A → Crash
User B → Works
User C → Works
```

Focus on:

* User profile
* Outlook profile
* Add-ins
* User-specific configuration
* Cached data
* Account-specific policies

---

# 30. Outlook Crashes for Multiple Users

Example:

```text
User A → Crash
User B → Crash
User C → Crash
```

Investigate:

* Office update
* Windows update
* Organization-wide add-in
* Microsoft 365 service
* Security software
* Endpoint configuration

A widespread issue should not be treated as an individual profile problem.

---

# 31. Same User, Different Computer

Example:

```text
Computer A
 ↓
Outlook Crashes

Computer B
 ↓
Outlook Works
```

This strongly suggests investigating:

* Computer A
* Office installation
* Windows
* Add-ins
* Local profile
* Local cached data

---

# 32. Different User, Same Computer

Example:

```text
Computer A

User A → Outlook Crashes
User B → Outlook Works
```

This suggests investigating:

* User profile
* Outlook profile
* User-specific configuration
* Authentication
* User-specific add-ins/settings

---

# 33. Outlook Repair

If approved troubleshooting indicates an Office installation problem, repair may be appropriate.

Typical repair options include:

```text
Office
 ↓
Repair
 ↓
Quick Repair
or
Online Repair
```

Follow company procedures because repair actions can affect installed Office components.

---

# 34. Update Outlook

Before performing disruptive remediation:

```text
Check Office Version
        ↓
Check Available Updates
        ↓
Review Known Issues
        ↓
Apply Approved Update
        ↓
Test
```

Document the version before and after remediation.

---

# 35. Reinstall Office

Reinstallation should generally be considered after less disruptive troubleshooting has been exhausted or when organizational procedures require it.

Before reinstalling:

* Document configuration
* Confirm licensing
* Confirm account access
* Confirm user data location
* Capture error information
* Follow approved deployment procedures

---

# 36. Outlook Crash Decision Tree

```text
                    Outlook Crash
                         ↓
               Does Outlook Web Work?
                  /             \
                Yes              No
                 ↓                ↓
          Desktop Investigation  Account /
                 ↓               Service
           Test Safe Mode
             /        \
          Works       Crashes
            ↓            ↓
         Add-ins     Profile
                      ↓
                    Office
                      ↓
                    Windows
                      ↓
                  Event Logs
                      ↓
                  Validate Fix
```

---

# 37. L1 Troubleshooting Checklist

```text
[ ] Confirm exact symptom
[ ] Determine crash frequency
[ ] Identify action causing crash
[ ] Check whether Outlook Web works
[ ] Restart Outlook
[ ] Check Windows resources
[ ] Test Outlook Safe Mode
[ ] Capture error message
[ ] Check whether other users are affected
[ ] Record Office version
[ ] Record Windows version
```

---

# 38. L2 Troubleshooting Checklist

```text
[ ] Analyze Safe Mode result
[ ] Investigate add-ins
[ ] Test Outlook profile
[ ] Check OST/cache
[ ] Check Event Viewer
[ ] Check Reliability Monitor
[ ] Check Office installation
[ ] Check Office updates
[ ] Check Windows updates
[ ] Compare affected vs working device
[ ] Compare affected vs working user
[ ] Check service health when appropriate
[ ] Apply approved remediation
[ ] Validate resolution
[ ] Document root cause
```

---

# 39. Scenario — Outlook Crashes at Startup

### Investigation

```text
Issue:
Outlook crashes shortly after opening.

Test:
Outlook Safe Mode.

Result:
Safe Mode opens successfully.

Finding:
Normal startup component is likely contributing to the crash.

Next Step:
Investigate installed add-ins and startup components.

Validation:
Normal Outlook starts successfully after approved remediation.
```

---

# 40. Scenario — Outlook Crashes When Opening Calendar

```text
Issue:
Outlook works normally until Calendar is opened.

Investigation:
Tested Outlook Web Calendar.
Web Calendar worked correctly.
Tested desktop Outlook behavior.
Reviewed add-ins and local profile.

Finding:
Issue isolated to the desktop client.

Action:
Applied approved client/profile remediation.

Validation:
Calendar opened successfully without a crash.
```

---

# 41. Scenario — Outlook Crashes After Office Update

```text
Issue:
Outlook started crashing after a recent Office update.

Investigation:
Recorded Office version and build.
Confirmed issue began after update.
Tested other users.
Checked organizational guidance and known issues.

Finding:
Issue correlated with the Office build.

Action:
Followed approved organizational remediation.

Validation:
Outlook operated normally after remediation.
```

---

# 42. Scenario — Outlook Crashes for One User

```text
Issue:
Only one user experiences Outlook crashes.

Investigation:
Outlook Web works.
Other users on the same computer environment work normally.
Safe Mode testing performed.
User-specific Outlook profile investigated.

Finding:
Issue isolated to the user's Outlook environment.

Action:
Created/tested an approved new Outlook profile.

Validation:
Outlook remained stable.
```

---

# 43. Scenario — Multiple Users Crash

```text
Issue:
Multiple users report Outlook crashes.

Investigation:
Compared Office versions.
Confirmed affected users received the same recent update.
Checked Microsoft 365 service health and organizational change records.

Finding:
Issue appeared organization-wide rather than user-specific.

Action:
Escalated according to the incident/change-management process.

Validation:
Confirmed Outlook stability after the organizational remediation.
```

---

# 44. Support Ticket Template

```text
Issue:
[Describe crash]

Affected User:
[User / Department]

Device:
[Computer / Asset]

Outlook Version:
[Version / Build]

Windows Version:
[Version]

Frequency:
[Every startup / intermittent / action-specific]

Trigger:
[What action causes crash]

Outlook Web:
[Works / Fails]

Safe Mode:
[Works / Fails]

Add-ins:
[Relevant information]

Event Viewer:
[Relevant crash information]

Investigation:
[Steps performed]

Root Cause:
[Confirmed cause]

Resolution:
[Approved remediation]

Validation:
[How the fix was confirmed]

Status:
[Resolved / Escalated]
```

---

# 45. Root Cause Categories

Classify the issue where possible:

### Application

* Outlook application
* Office installation
* Office update

### Add-in

* Meeting integration
* CRM
* Security integration
* Productivity tool

### Profile

* Outlook profile
* User configuration

### Local Data

* OST
* Cached data
* Search/indexing

### Windows

* Operating system
* System resources
* Windows update

### Environment

* Network
* Security software
* Endpoint configuration

### Service

* Microsoft 365
* Exchange Online

---

# 46. Best Practices

### Do

* Capture the exact crash pattern.
* Test Outlook Web.
* Use Safe Mode for isolation.
* Review Event Viewer and Reliability Monitor.
* Compare affected and working environments.
* Check recent Office/Windows changes.
* Investigate add-ins systematically.
* Document evidence.
* Apply approved remediation.
* Validate after the fix.

### Don't

* Immediately reinstall Office.
* Immediately recreate the profile.
* Delete cached data without justification.
* Disable security software without authorization.
* Disable MFA or Conditional Access.
* Assume the first suspected component is the root cause.
* Close the incident without validating the fix.

---

# 47. Key Takeaways

* Outlook crashes can originate from multiple layers.
* Safe Mode is an important diagnostic tool.
* Add-ins are a common area to investigate.
* Outlook Web helps isolate desktop client problems.
* Event Viewer and Reliability Monitor provide useful evidence.
* A crash after an update should be investigated as a potential change-related issue.
* Compare affected and working users/devices.
* Do not confuse a suspected faulting module with a confirmed root cause.
* Always document the trigger, evidence, remediation, and validation.

---

## Related Documentation

* [Outlook Overview](./01-Outlook-Overview.md)
* [Outlook Profile](./04-Outlook-Profile.md)
* [Outlook Profile Creation](./05-Outlook-Profile-Creation.md)
* [Outlook Profile Corruption](./06-Outlook-Profile-Corruption.md)
* [Shared Mailbox](./17-Shared-Mailbox.md)
* [Credential Prompts](./20-Credential-Prompts.md)
* [Outlook Connectivity](./21-Outlook-Connectivity.md)
* [Outlook Performance](./22-Outlook-Performance.md)
* [Mail Send/Receive Issues](./23-Mail-Send-Receive-Issues.md)
* [Real-World Scenarios](./25-Real-World-Scenarios.md)
