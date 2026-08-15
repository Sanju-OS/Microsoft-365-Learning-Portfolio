# Outlook Real-World Scenarios

## 1. Purpose

This document contains practical Microsoft Outlook support scenarios designed to demonstrate an L1/L2 troubleshooting approach.

Each scenario follows a structured support methodology:

```text
User Report
    ↓
Understand the Symptoms
    ↓
Identify Scope
    ↓
Collect Evidence
    ↓
Troubleshoot
    ↓
Identify Root Cause
    ↓
Apply Approved Resolution
    ↓
Validate
    ↓
Document
    ↓
Close / Escalate
````

The objective is not to immediately apply a fix.

The objective is to identify **where the failure occurs and why**.

---

# 2. Scenario — Outlook Keeps Asking for Password

## User Report

> "Outlook keeps asking me for my password."

## Symptoms

* Outlook repeatedly prompts for credentials.
* User enters the correct password.
* Prompt appears again.
* Outlook may show disconnected status.

## Initial Checks

```text
1. Check Internet
2. Test Microsoft 365 Web Login
3. Check Outlook Connection
4. Check MFA
5. Check account status
6. Check Conditional Access where applicable
7. Check Outlook profile
```

## Isolation

```text
Outlook Web
    ↓
Login Successful?
```

If Web login works:

```text
Microsoft 365 Account
        ↓
Likely Working
        ↓
Investigate Outlook Desktop
```

## Possible Causes

* Authentication token issue
* Cached credentials
* Outlook profile problem
* Conditional Access
* MFA issue
* Network/proxy problem

## Resolution

Apply the organization's approved authentication/profile remediation.

## Validation

```text
Outlook
 ↓
Sign In
 ↓
No Repeated Prompt
 ↓
Connected
```

## Support Classification

**Identity / Authentication / Outlook Client**

---

# 3. Scenario — Outlook Shows Disconnected

## User Report

> "Outlook is showing Disconnected."

## Investigation

Check:

```text
Internet
 ↓
Outlook Web
 ↓
Authentication
 ↓
VPN
 ↓
Network
 ↓
Outlook Profile
```

## Test

If Outlook Web works:

```text
OWA → Works
Desktop → Disconnected
```

Focus on the local Outlook environment.

## Possible Causes

* Network problem
* VPN
* Authentication
* Outlook profile
* Autodiscover
* Local client issue

## Resolution

Apply the appropriate approved remediation based on evidence.

## Validation

```text
Outlook
 ↓
Connected
 ↓
Send Test Email
 ↓
Receive Test Email
```

---

# 4. Scenario — Email Stuck in Outbox

## User Report

> "My email is stuck in the Outbox."

## Investigation

Check:

* Outlook connection
* Message size
* Attachment
* Authentication
* Network
* Outlook Web

## Isolation Test

Send a new email without attachment.

```text
New Email
 ↓
Successfully Sent
```

If successful, investigate the original message.

## Possible Cause

* Large attachment
* Corrupted message
* Outlook client issue
* Network interruption

## Validation

Send a test message and confirm delivery.

---

# 5. Scenario — User Cannot Send Email

## User Report

> "I can receive emails, but I cannot send anything."

## Initial Assessment

```text
Receive → Works
Send → Fails
```

## Troubleshooting

Check:

```text
Outlook Connection
 ↓
Outbox
 ↓
Internal Recipient
 ↓
External Recipient
 ↓
NDR
```

## Test

Send to an internal user.

If successful:

```text
Internal → Works
External → Fails
```

Investigate external mail flow.

## Possible Causes

* Recipient issue
* Mail flow restriction
* Transport rule
* Authentication
* Attachment size
* External delivery restriction

---

# 6. Scenario — User Cannot Receive Email

## User Report

> "I'm not receiving new emails."

## Investigation

Check:

```text
Inbox
 ↓
Junk
 ↓
Other Folders
 ↓
Rules
 ↓
Search
 ↓
Outlook Web
```

## Test

Send a test email from another internal user.

Then send from an external account.

## Possible Result

```text
Internal → Works
External → Fails
```

This indicates that external mail flow should be investigated.

---

# 7. Scenario — Outlook Web Has Email but Desktop Does Not

## User Report

> "I can see the email on Outlook Web but not in Outlook Desktop."

## Investigation

```text
Mailbox
 ↓
Contains Email
```

Therefore:

```text
Exchange Online
 ↓
Likely Working
```

Focus on:

* Outlook synchronization
* Cached mailbox data
* Outlook profile
* Connectivity
* Local client

## Validation

Confirm the email appears in Outlook Desktop after remediation.

---

# 8. Scenario — Outlook Desktop Is Slow

## User Report

> "Outlook is very slow."

## Questions

Ask:

* When did it start?
* Is the entire computer slow?
* Is Outlook Web fast?
* Does Safe Mode improve performance?
* Was an add-in recently installed?
* Was Office recently updated?

## Investigation

```text
Windows Resources
 ↓
Network
 ↓
Outlook Web
 ↓
Safe Mode
 ↓
Add-ins
 ↓
Profile
 ↓
Cached Data
```

## Possible Causes

* Add-in
* Large mailbox
* Local cache
* Profile
* Windows resources
* Network

---

# 9. Scenario — Outlook Freezes

## User Report

> "Outlook freezes whenever I open it."

## First Test

Start Outlook in Safe Mode.

```text
Safe Mode
 ↓
Works
```

This suggests investigating:

* Add-ins
* Startup components
* Custom configuration

If Safe Mode also fails:

```text
Profile
 ↓
Office
 ↓
Windows
 ↓
Local Data
```

---

# 10. Scenario — Outlook Crashes at Startup

## User Report

> "Outlook opens and immediately closes."

## Investigation

```text
Outlook Web
 ↓
Works?

Safe Mode
 ↓
Works?
```

If Safe Mode works:

```text
Investigate Add-ins
```

If Safe Mode also crashes:

```text
Investigate Profile
 ↓
Office
 ↓
Windows
```

## Validation

Restart Outlook normally and confirm stability.

---

# 11. Scenario — Outlook Crashes When Opening Attachment

## User Report

> "Outlook crashes whenever I open an attachment."

## Investigation

Determine:

```text
All Attachments?
       OR
Specific Attachment Type?
```

Test different files.

## Example

```text
PDF → Works
Word → Works
Excel → Crashes
```

Focus on:

* Office integration
* Add-ins
* File preview
* Office installation

---

# 12. Scenario — Outlook Search Does Not Find Emails

## User Report

> "I know the email exists, but Outlook search cannot find it."

## Investigation

Check:

```text
Search Scope
 ↓
Search Filters
 ↓
Mailbox
 ↓
Indexing
 ↓
Outlook Profile
```

Compare with Outlook Web.

## Result

```text
Outlook Web Search → Finds Email
Desktop Search → Does Not
```

Focus on local search/indexing.

---

# 13. Scenario — Deleted Email Needs Recovery

## User Report

> "I accidentally deleted an important email."

## Initial Investigation

Check:

```text
Deleted Items
 ↓
Search
 ↓
Recoverable Items / Approved Recovery Process
```

Determine:

* When it was deleted
* Which folder it was in
* Whether it was permanently deleted
* Whether organizational retention/recovery policies apply

## Important

Do not promise recovery before confirming the available recovery options.

## Validation

Confirm the recovered message is accessible to the user.

---

# 14. Scenario — Shared Mailbox Not Appearing

## User Report

> "I have access to the shared mailbox, but it isn't appearing in Outlook."

## Investigation

Check:

```text
User Permissions
 ↓
Full Access
 ↓
Automapping
 ↓
Outlook
 ↓
Outlook Web
```

## Isolation

If the shared mailbox appears in Outlook Web but not Desktop:

```text
Likely Desktop Configuration
```

If it does not appear anywhere:

```text
Investigate Permissions
```

---

# 15. Scenario — User Cannot Send From Shared Mailbox

## User Report

> "I can open the shared mailbox, but I cannot send from it."

## Investigation

Check:

```text
Full Access
        +
Send As / Send on Behalf
```

Having access to a mailbox does not necessarily mean the user has every sending permission.

## Validation

Send a controlled test message from the shared mailbox and confirm the expected sender identity.

---

# 16. Scenario — Distribution Group Email Fails

## User Report

> "I cannot send email to the distribution group."

## Investigation

Check:

* Group address
* Sender restrictions
* Group membership
* External sender restrictions
* Message size
* NDR
* Mail flow

## Important

Analyze the NDR before changing configuration.

---

# 17. Scenario — External Email Not Received

## User Report

> "Internal email works, but emails from external companies are not arriving."

## Test

```text
Internal Sender → User
        ↓
Works

External Sender → User
        ↓
Fails
```

Investigate:

```text
External Mail
 ↓
Exchange Online
 ↓
Anti-Spam / Security
 ↓
Mail Flow
 ↓
Mailbox
```

Check approved security and mail-flow tools.

---

# 18. Scenario — Emails Going to Junk

## User Report

> "Important emails are going to Junk."

## Investigation

Check:

* Junk folder
* Sender information
* Blocked senders
* Safe senders
* Mail flow/security filtering
* Organization policies

## Important

Do not disable spam protection simply to solve an individual delivery issue.

---

# 19. Scenario — Email Automatically Moves to Another Folder

## User Report

> "Emails keep disappearing from my Inbox."

## Investigation

Check:

```text
Inbox
 ↓
Rules
 ↓
Archive
 ↓
Junk
 ↓
Deleted Items
 ↓
Search
```

## Possible Cause

An Outlook rule may be automatically moving the message.

See:

[Rules](./08-Rules.md)

---

# 20. Scenario — Outlook Works on Home Network but Not Corporate Network

## User Report

> "Outlook works at home but not in the office."

## Investigation

Compare:

```text
Home Network
 ↓
Outlook Works

Corporate Network
 ↓
Outlook Fails
```

Investigate:

* DNS
* Proxy
* Firewall
* Network routing
* Security inspection
* VPN

## Escalation

Provide the network team with:

* User
* Device
* Time of failure
* Error
* Network used
* Test results

---

# 21. Scenario — Outlook Works Without VPN but Not With VPN

## Investigation

```text
VPN OFF
 ↓
Works

VPN ON
 ↓
Fails
```

Focus on:

* VPN routing
* DNS
* Proxy
* Network security
* VPN gateway

Do not modify enterprise VPN settings without authorization.

---

# 22. Scenario — Multiple Users Cannot Send Email

## Symptoms

```text
User A → Cannot Send
User B → Cannot Send
User C → Cannot Send
```

This is unlikely to be three independent Outlook profile problems.

Investigate:

```text
Exchange Online
 ↓
Mail Flow
 ↓
Microsoft 365 Service Health
 ↓
Organization Network
```

## Support Approach

Treat as a potential widespread incident.

---

# 23. Scenario — Outlook Problem After Office Update

## User Report

> "Outlook started crashing after the latest update."

## Investigation

Collect:

* Office version
* Build
* Update date
* Number of affected users
* Crash symptoms

Compare:

```text
Before Update → Normal
After Update → Crash
```

Check approved organizational guidance and known issues.

---

# 24. Scenario — Outlook Problem After Password Change

## User Report

> "I changed my Microsoft 365 password and Outlook stopped working."

## Investigation

```text
Password Changed
 ↓
Authentication
 ↓
Outlook
```

Check:

* Microsoft 365 Web login
* MFA
* Authentication prompts
* Outlook connection
* Cached authentication
* Account status

---

# 25. Scenario — Calendar Not Updating

## User Report

> "My Outlook calendar is not showing recent meetings."

## Investigation

Compare:

```text
Outlook Web Calendar
        vs
Outlook Desktop Calendar
```

If Web is current:

```text
Mailbox → Working
Desktop Synchronization → Investigate
```

If Web is also incorrect:

```text
Mailbox / Calendar / Service Investigation
```

---

# 26. Scenario — Meeting Invitation Not Received

## User Report

> "Someone sent me a meeting invitation, but I didn't receive it."

## Investigation

Check:

```text
Inbox
 ↓
Junk
 ↓
Deleted Items
 ↓
Rules
 ↓
Calendar
 ↓
Search
```

Then test another meeting invitation.

Investigate mail flow if necessary.

---

# 27. Scenario — User Cannot Find Old Email

## User Report

> "I cannot find an email from two years ago."

## Investigation

Check:

* Search scope
* Archive
* PST
* Online Archive where applicable
* Deleted Items
* Retention policies
* Other folders

See:

[Archive](./15-Archive.md)

[PST Files](./16-PST-Files.md)

---

# 28. Scenario — PST File Cannot Be Opened

## User Report

> "I cannot open my PST file."

## Investigation

Check:

* File location
* File accessibility
* File size
* File permissions
* Whether the PST is stored on unsupported/network storage
* File integrity

Follow approved data-recovery procedures.

Do not overwrite the original PST during troubleshooting.

---

# 29. Scenario — Outlook Profile Corruption

## Symptoms

* Outlook crashes
* Outlook freezes
* Mailbox does not synchronize
* Repeated connection problems
* Missing folders

## Investigation

Compare:

```text
Existing Profile
 ↓
Problem

New Test Profile
 ↓
Works
```

## Conclusion

A profile-level problem becomes a strong possibility.

See:

[Outlook Profile Corruption](./06-Outlook-Profile-Corruption.md)

---

# 30. Scenario — User Says "Outlook Is Down"

Never accept "Outlook is down" as enough information.

Clarify:

```text
Can Outlook Open?
Can User Sign In?
Can User Send?
Can User Receive?
Can Outlook Web Open?
Can Teams Work?
Are Other Users Affected?
```

Convert the general complaint into a specific technical symptom.

---

# 31. Scenario — Outlook Web and Desktop Both Fail

## Investigation

```text
OWA → Fails
Desktop → Fails
```

Focus on:

```text
Account
 ↓
Authentication
 ↓
Conditional Access
 ↓
Exchange Online
 ↓
Microsoft 365 Service
```

Avoid starting with local profile remediation.

---

# 32. Scenario — Only One Computer Is Affected

```text
User
 ↓
Computer A → Outlook Fails
Computer B → Outlook Works
```

Focus on:

* Windows
* Office installation
* Outlook profile
* Add-ins
* Local cache
* Device configuration

---

# 33. Scenario — Same Computer, Another User Works

```text
Computer
 ↓
User A → Outlook Fails
User B → Outlook Works
```

Focus on:

* User profile
* Outlook profile
* Account
* User-specific configuration

---

# 34. Scenario — Multiple Computers and Users Are Affected

```text
User A / Computer A → Fails
User B / Computer B → Fails
User C / Computer C → Fails
```

Investigate:

* Microsoft 365 service health
* Exchange Online
* Office update
* Windows update
* Organization-wide configuration
* Network

Treat this as a potential major incident.

---

# 35. L1 Troubleshooting Methodology

A good L1 workflow:

```text
1. Listen
2. Clarify
3. Reproduce
4. Check obvious causes
5. Test Outlook Web
6. Check connectivity
7. Apply approved basic remediation
8. Validate
9. Document
10. Escalate if required
```

---

# 36. L2 Troubleshooting Methodology

A good L2 workflow:

```text
1. Review L1 investigation
2. Reproduce the issue
3. Determine scope
4. Compare working vs affected environment
5. Isolate the failure layer
6. Analyze logs/errors
7. Investigate configuration
8. Identify root cause
9. Apply approved remediation
10. Validate
11. Document
12. Provide RCA when required
```

---

# 37. Evidence Collection

Good support engineers collect evidence.

Examples:

```text
User:
[User]

Device:
[Asset / Computer]

Time:
[Date / Time]

Error:
[Exact message]

Outlook Version:
[Version]

Windows Version:
[Version]

Network:
[Office / Home / VPN]

OWA:
[Works / Fails]

Safe Mode:
[Works / Fails]

Affected Users:
[Number]

Actions:
[Steps performed]
```

---

# 38. Root Cause vs Symptom

### Symptom

> Outlook is disconnected.

### Root Cause

> Authentication token could not be refreshed.

---

### Symptom

> Outlook is slow.

### Root Cause

> An installed add-in was causing excessive Outlook processing.

---

### Symptom

> Email is missing.

### Root Cause

> An Outlook rule moved the message to another folder.

Always try to distinguish the symptom from the confirmed cause.

---

# 39. Resolution vs Workaround

### Resolution

Fixes the underlying problem.

### Workaround

Provides an alternative way to continue working.

Example:

```text
Outlook Desktop
 ↓
Fails

Outlook Web
 ↓
Works
```

OWA can be a useful workaround while the desktop issue is investigated.

Document the difference.

---

# 40. Escalation Example

Escalate when:

* Required permissions are unavailable
* Mail-flow configuration needs admin access
* Network infrastructure is involved
* Microsoft 365 service incident is suspected
* Security policy needs modification
* Issue requires vendor support
* Multiple users are affected
* Business impact is high

Provide complete troubleshooting evidence.

---

# 41. Good Escalation Example

```text
Issue:
Multiple users cannot send external email.

Impact:
15 users across Sales department.

Internal Email:
Working.

External Email:
Failing.

Outlook Web:
Working.

NDR:
[Relevant error]

Investigation:
Confirmed issue across multiple users and devices.
Internal mail flow successful.
External delivery failing.

Suspected Layer:
Exchange Online outbound mail flow.

Requested Action:
Please investigate outbound mail-flow configuration/restrictions.
```

This is much better than:

> "Outlook is not working. Please check."

---

# 42. Incident Documentation

A professional incident should contain:

```text
Incident
 ↓
Impact
 ↓
Timeline
 ↓
Symptoms
 ↓
Investigation
 ↓
Root Cause
 ↓
Resolution
 ↓
Validation
 ↓
Prevention
```

---

# 43. Root Cause Analysis Example

## Incident

Multiple users could not send external email.

## Impact

Sales users were unable to communicate with external customers.

## Root Cause

Outbound mail-flow configuration prevented the affected messages from being delivered.

## Resolution

The responsible configuration was corrected through the approved change process.

## Validation

Internal and external test emails were successfully delivered.

## Prevention

Document the configuration and include appropriate validation in future changes.

---

# 44. Scenario Classification

Use these categories when documenting incidents:

| Category       | Example                 |
| -------------- | ----------------------- |
| Authentication | Password prompts        |
| Connectivity   | Outlook disconnected    |
| Profile        | Corrupted profile       |
| Performance    | Outlook slow            |
| Application    | Outlook crash           |
| Mail Flow      | External email failure  |
| Mailbox        | Missing email           |
| Permissions    | Shared mailbox access   |
| Search         | Email not found         |
| Calendar       | Meeting synchronization |
| Configuration  | Rules / signatures      |
| Endpoint       | Windows / Office issue  |

---

# 45. L1 vs L2 Example

## L1

```text
User reports Outlook disconnected.

L1:
- Check Internet
- Check Outlook status
- Test OWA
- Restart Outlook
- Capture error
- Perform approved basic remediation
```

## L2

```text
L1 escalation received.

L2:
- Analyze authentication
- Investigate Autodiscover
- Compare working/affected systems
- Check profile
- Investigate network
- Analyze logs
- Identify root cause
- Apply approved remediation
```

---

# 46. Communication With the User

Avoid saying:

> "I don't know."

Instead say:

> "I'm going to isolate whether this is an Outlook client, network, authentication, or Microsoft 365 service issue."

After resolution:

> "The issue was isolated to the Outlook client configuration. The configuration was corrected and we confirmed that sending, receiving, and synchronization are now working."

Clear communication builds user confidence.

---

# 47. Ticket Closure Example

```text
Resolution Summary:

The user's Outlook desktop client was unable to synchronize correctly.

Investigation confirmed that Outlook Web was functioning normally, isolating the issue to the desktop environment.

The Outlook client configuration was remediated according to the approved support procedure.

Validation confirmed:
- Outlook connected successfully
- New emails synchronized
- Email sending worked
- Email receiving worked

User confirmed normal functionality.

Status: Resolved
```

---

# 48. Troubleshooting Principles

## Principle 1 — Isolate

Find where the problem exists.

## Principle 2 — Compare

Compare working and affected environments.

## Principle 3 — Evidence

Do not guess the root cause.

## Principle 4 — Least Disruptive

Start with low-risk troubleshooting.

## Principle 5 — Validate

Always confirm the fix.

## Principle 6 — Document

Record what happened and what was done.

## Principle 7 — Escalate Properly

Provide evidence rather than simply transferring the ticket.

---

# 49. Master Outlook Troubleshooting Flow

```text
                    User Reports Issue
                           ↓
                    Identify Symptom
                           ↓
                  Determine Scope
                           ↓
              Outlook Desktop or Web?
                     /           \
                  Desktop        Both
                     ↓             ↓
              Test Outlook Web   Account /
                     ↓           Service
               Check Network
                     ↓
              Authentication
                     ↓
                Outlook Client
                     ↓
                Profile
                     ↓
                 Add-ins
                     ↓
               OST / Cache
                     ↓
                Office
                     ↓
                 Windows
                     ↓
              Microsoft 365
                     ↓
                Mail Flow
                     ↓
               Root Cause
                     ↓
                Resolution
                     ↓
                Validation
                     ↓
               Documentation
```

---

# 50. Final Support Checklist

Before closing an Outlook incident:

```text
[ ] User's original symptom understood
[ ] Scope identified
[ ] Error captured
[ ] Outlook Web tested
[ ] Network checked
[ ] Authentication checked
[ ] Relevant configuration checked
[ ] Appropriate troubleshooting performed
[ ] Root cause identified or escalation documented
[ ] Approved remediation applied
[ ] Send tested
[ ] Receive tested
[ ] Calendar tested where relevant
[ ] User confirmed resolution
[ ] Ticket documented
```

---

# 51. Key Takeaways

* Do not troubleshoot based only on the user's initial description.
* Convert "Outlook is not working" into a specific technical symptom.
* Use Outlook Web to isolate desktop problems.
* Compare affected and working environments.
* Separate client problems from mailbox and mail-flow problems.
* Use evidence to determine the root cause.
* Apply the least disruptive appropriate remediation.
* Validate the fix before closing the ticket.
* Document troubleshooting clearly.
* Escalate with complete technical information.

---

## Related Documentation

* [Outlook Overview](./01-Outlook-Overview.md)
* [Outlook Configuration](./02-Outlook-Configuration.md)
* [Outlook Account Setup](./03-Outlook-Account-Setup.md)
* [Outlook Profile](./04-Outlook-Profile.md)
* [Outlook Profile Creation](./05-Outlook-Profile-Creation.md)
* [Outlook Profile Corruption](./06-Outlook-Profile-Corruption.md)
* [Email Management](./07-Email-Management.md)
* [Rules](./08-Rules.md)
* [Calendar](./11-Calendar.md)
* [Search](./14-Search.md)
* [Archive](./15-Archive.md)
* [PST Files](./16-PST-Files.md)
* [Shared Mailbox](./17-Shared-Mailbox.md)
* [Distribution Groups](./18-Distribution-Groups.md)
* [Autodiscover](./19-Autodiscover.md)
* [Credential Prompts](./20-Credential-Prompts.md)
* [Outlook Connectivity](./21-Outlook-Connectivity.md)
* [Outlook Performance](./22-Outlook-Performance.md)
* [Mail Send/Receive Issues](./23-Mail-Send-Receive-Issues.md)
* [Outlook Crash Issues](./24-Outlook-Crash-Issues.md)

