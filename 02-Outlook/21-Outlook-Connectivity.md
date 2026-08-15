# Outlook Connectivity

## 1. Overview

Outlook connectivity refers to the ability of the Outlook client to communicate successfully with Microsoft 365 services, Exchange Online, and the user's mailbox.

A simplified connection flow is:

```text
User
  ↓
Outlook Desktop
  ↓
Internet / Network
  ↓
Authentication
  ↓
Microsoft 365
  ↓
Exchange Online
  ↓
User Mailbox
````

Connectivity problems can affect:

* Sending email
* Receiving email
* Calendar
* Contacts
* Shared mailboxes
* Address book
* Free/busy information
* Outlook search
* Synchronization

---

# 2. Common Outlook Connectivity Symptoms

Users may report:

* Outlook shows Disconnected
* Outlook shows Working Offline
* Outlook keeps connecting and disconnecting
* New emails are not arriving
* Emails remain in Outbox
* Send/Receive fails
* Calendar does not update
* Outlook works on the web but not desktop
* Outlook works on one network but not another
* Outlook repeatedly asks for credentials

---

# 3. Outlook Connection States

Common Outlook status indicators include:

```text
Connected
Connecting
Disconnected
Working Offline
Need Password
```

These states provide useful troubleshooting clues.

Do not treat the status message as the root cause by itself.

---

# 4. Connected

Example:

```text
Outlook
   ↓
Connected
   ↓
Exchange Online
```

The client has an active connection.

If email is still not updating, investigate other layers such as:

* Synchronization
* Mail flow
* Outlook rules
* Mailbox issues
* Service-side problems

---

# 5. Connecting

Example:

```text
Outlook
   ↓
Connecting...
   ↓
Exchange Online
```

If Outlook remains stuck on "Connecting", investigate:

```text
Network
 ↓
Authentication
 ↓
DNS
 ↓
Exchange Online
 ↓
Outlook Profile
```

---

# 6. Disconnected

When Outlook displays:

```text
Disconnected
```

the client is not currently communicating successfully with the required service.

Possible causes include:

* Internet failure
* Network instability
* Authentication problem
* VPN issue
* Proxy issue
* DNS problem
* Outlook profile problem
* Exchange Online service issue

---

# 7. Working Offline

"Working Offline" can be intentional or accidental.

Example:

```text
Outlook
   ↓
Working Offline
```

First determine whether the user manually enabled offline mode.

If not, investigate:

```text
Connection
 ↓
Outlook Configuration
 ↓
Authentication
 ↓
Exchange Connectivity
```

---

# 8. Need Password

A "Need Password" state may indicate an authentication problem.

Related troubleshooting:

```text
Need Password
      ↓
Test Microsoft 365 Web Login
      ↓
Works?
   /       \
 Yes        No
 ↓           ↓
Desktop     Identity /
Issue       Authentication
```

See:

[Credential Prompts](./20-Credential-Prompts.md)

---

# 9. First Troubleshooting Question

Ask:

> "Does Outlook Web work?"

This is one of the most useful isolation tests.

```text
Outlook Web
     ↓
   Works?
   /    \
 Yes     No
 ↓        ↓
Desktop   Account /
Issue     Service
```

---

# 10. Outlook Web Works

Example:

```text
Outlook Web
     ↓
Works

Outlook Desktop
     ↓
Disconnected
```

This suggests investigating the local environment.

Check:

* Outlook profile
* Network
* Cached authentication
* Office installation
* Outlook configuration
* VPN/proxy
* Autodiscover

---

# 11. Outlook Web Also Fails

Example:

```text
Outlook Web
     ↓
Fails

Outlook Desktop
     ↓
Fails
```

Investigate broader areas:

```text
User Account
 ↓
Authentication
 ↓
Microsoft 365
 ↓
Exchange Online
```

Do not immediately rebuild Outlook.

---

# 12. Check Internet Connectivity

Before performing advanced troubleshooting:

```text
Computer
   ↓
Internet
   ↓
Microsoft 365
```

Check whether other Internet-dependent applications work.

For example:

* Browser
* Microsoft 365 web applications
* Teams
* Other approved business services

If the computer has no Internet access, Outlook troubleshooting should begin with network connectivity.

---

# 13. Check Network Stability

An unstable connection can cause:

```text
Connected
   ↓
Disconnected
   ↓
Connecting
   ↓
Connected
```

Ask:

* Does the problem happen continuously?
* Does it happen when switching Wi-Fi?
* Does it happen after waking the computer?
* Does it happen only on VPN?
* Does it happen only on a particular network?

The pattern is useful evidence.

---

# 14. Wi-Fi Troubleshooting

If the issue occurs on Wi-Fi:

```text
Wi-Fi
 ↓
Internet
 ↓
Microsoft 365
 ↓
Outlook
```

Compare:

```text
Wi-Fi
   vs
Ethernet
```

If Outlook works on Ethernet but not Wi-Fi, investigate the network rather than immediately rebuilding the Outlook profile.

---

# 15. VPN Troubleshooting

VPNs can change:

* Routing
* DNS
* Proxy
* Network access

Example:

```text
VPN ON
 ↓
Outlook Works

VPN OFF
 ↓
Outlook Fails
```

or:

```text
VPN ON
 ↓
Outlook Fails

VPN OFF
 ↓
Outlook Works
```

This provides useful evidence for network troubleshooting.

---

# 16. Proxy Troubleshooting

Corporate proxy configurations can affect Microsoft 365 connectivity.

Conceptually:

```text
Outlook
 ↓
Proxy
 ↓
Internet
 ↓
Microsoft 365
```

If browser access works but Outlook does not, compare application network behavior and organizational proxy configuration.

Do not change enterprise proxy settings without authorization.

---

# 17. DNS

DNS helps applications locate services.

A simplified flow is:

```text
Outlook
 ↓
DNS
 ↓
Microsoft 365 Service
 ↓
Connection
```

DNS problems can cause:

* Connection failures
* Autodiscover problems
* Intermittent connectivity
* Authentication-related symptoms

Related documentation:

[Autodiscover](./19-Autodiscover.md)

---

# 18. Authentication

Outlook connectivity depends on successful authentication.

Simplified:

```text
Outlook
 ↓
Microsoft Entra ID
 ↓
Authentication
 ↓
Microsoft 365
 ↓
Exchange Online
```

If authentication fails, Outlook may show:

* Need Password
* Disconnected
* Sign-in required

---

# 19. MFA and Connectivity

MFA may affect the authentication process.

Example:

```text
Outlook
 ↓
Authentication
 ↓
MFA
 ↓
Token
 ↓
Microsoft 365
```

If authentication cannot complete, Outlook may not establish the required connection.

---

# 20. Conditional Access

Conditional Access can evaluate access conditions.

Example:

```text
User
 ↓
Application
 ↓
Device
 ↓
Conditional Access
 ↓
Allow / Block / Require Action
```

If access is blocked, investigate the applicable policy rather than disabling security controls.

---

# 21. Outlook Profile

A damaged profile can cause connectivity problems.

Symptoms may include:

* Outlook repeatedly connecting
* Outlook disconnecting
* Authentication problems
* Synchronization failures
* Missing mailbox data

A useful test is:

```text
Existing Profile
       ↓
Problem
       ↓
Test New Profile
       ↓
Works?
```

If the new profile works, the old profile may be the cause.

---

# 22. New Profile Test

Do not create a new profile immediately.

First collect evidence.

Recommended sequence:

```text
Confirm Issue
      ↓
Test Outlook Web
      ↓
Check Network
      ↓
Check Authentication
      ↓
Test Existing Profile
      ↓
Create New Profile if Appropriate
```

---

# 23. Cached Mode

Outlook desktop commonly uses cached data to provide offline access and improve performance.

Conceptually:

```text
Exchange Online
      ↓
Cached Mailbox Data
      ↓
Outlook
```

Synchronization problems can occur between the local cache and the server mailbox.

---

# 24. Synchronization vs Connectivity

These are related but different.

### Connectivity

Can Outlook communicate with the service?

### Synchronization

Is mailbox data being correctly synchronized?

Example:

```text
Connected
   ↓
But new email missing
```

This does not automatically mean the connection is down.

Investigate synchronization and mailbox behavior.

---

# 25. Email Stuck in Outbox

### User Report

> "My email is stuck in the Outbox."

Possible areas:

```text
Outbox
 ↓
Outlook Connection
 ↓
Authentication
 ↓
Exchange Online
 ↓
Mail Flow
```

Check:

* Outlook connection state
* Network
* Attachment size
* Authentication
* Mail flow
* Outlook client

---

# 26. Send/Receive Failure

If Outlook cannot send or receive:

```text
Send/Receive
      ↓
Connection
      ↓
Authentication
      ↓
Exchange Online
```

Capture the exact error message.

Avoid guessing the root cause from the symptom alone.

---

# 27. Calendar Not Updating

Calendar synchronization may also be affected by connectivity or synchronization issues.

Example:

```text
Outlook Desktop
      ↓
Calendar
      ↓
Exchange Online
```

Compare with Outlook Web:

```text
Desktop Calendar
       vs
Web Calendar
```

If Web is current but Desktop is not, investigate the local Outlook client.

---

# 28. Shared Mailbox Connectivity

If a shared mailbox is affected:

```text
User
 ↓
Outlook
 ↓
Shared Mailbox
```

Check:

* User permissions
* Full Access
* Outlook client
* Automapping
* Outlook Web

Related documentation:

[Shared Mailbox](./17-Shared-Mailbox.md)

---

# 29. Distribution Group vs Connectivity

If a user cannot send to a distribution group, do not automatically assume Outlook connectivity is the problem.

Check:

```text
Outlook
 ↓
Can Send?
 ↓
Group
 ↓
Delivery
```

If the email leaves Outlook successfully but is rejected later, investigate mail flow and group configuration.

Related documentation:

[Distribution Groups](./18-Distribution-Groups.md)

---

# 30. Outlook Web Comparison

A useful L2 test:

```text
                    Issue
                      ↓
              Test Outlook Web
                 /          \
              Works          Fails
               ↓               ↓
         Desktop issue     Broader issue
```

This dramatically narrows the troubleshooting scope.

---

# 31. Compare Another User

If possible, compare:

```text
Affected User
      vs
Working User
```

Compare:

* Same network?
* Same Microsoft 365 service?
* Same device type?
* Same Outlook version?
* Same policies?
* Same permissions?

This is a powerful troubleshooting method.

---

# 32. Compare Another Computer

Another useful test:

```text
User
 ↓
Computer A
 ↓
Outlook Fails

Same User
 ↓
Computer B
 ↓
Outlook Works
```

This strongly suggests a device/client issue.

---

# 33. Same Computer, Different User

Another useful test:

```text
Computer A
 ↓
User A → Outlook Fails
User B → Outlook Works
```

This may indicate:

* User profile
* Account configuration
* Authentication
* Outlook profile
* User-specific policy

---

# 34. Microsoft 365 Service Health

If multiple users suddenly lose Outlook connectivity:

```text
User A → Fails
User B → Fails
User C → Fails
```

Check the organization's Microsoft 365 service-health information.

Do not assume that every widespread Outlook issue is caused by local computers.

---

# 35. Service Issue Pattern

A service-side problem may look like:

```text
Multiple Users
      ↓
Multiple Devices
      ↓
Same Microsoft 365 Service
      ↓
Similar Symptoms
```

This pattern should trigger service-level investigation.

---

# 36. Outlook Connectivity Decision Tree

```text
                 Outlook Connectivity Issue
                           ↓
                  Is Internet Working?
                     /            \
                   Yes             No
                    ↓               ↓
             Test Outlook Web     Network
                    ↓            Troubleshooting
                Works?
                /    \
              Yes     No
               ↓       ↓
        Desktop Issue  Account /
               ↓       Service
          Check Profile
               ↓
         Authentication
               ↓
          DNS / Network
               ↓
        Exchange Online
```

---

# 37. L1 Troubleshooting Checklist

```text
[ ] Confirm exact symptom
[ ] Check Outlook connection status
[ ] Check Internet
[ ] Test Outlook Web
[ ] Check Microsoft 365 sign-in
[ ] Check whether password changed
[ ] Check MFA
[ ] Restart Outlook
[ ] Check VPN
[ ] Check network
[ ] Capture error message
```

---

# 38. L2 Troubleshooting Checklist

```text
[ ] Compare Web vs Desktop
[ ] Compare affected vs working user
[ ] Compare affected vs working computer
[ ] Check DNS
[ ] Check proxy
[ ] Check VPN
[ ] Check authentication
[ ] Check Conditional Access
[ ] Check Autodiscover
[ ] Investigate Outlook profile
[ ] Investigate cached synchronization
[ ] Check service health
[ ] Validate remediation
[ ] Document root cause
```

---

# 39. Scenario — Outlook Disconnected

### Incident

> "Outlook says Disconnected."

Investigation:

```text
1. Check Internet
2. Test Outlook Web
3. Check authentication
4. Check VPN
5. Check DNS/network
6. Check Outlook profile
7. Check Microsoft 365 service health
```

Do not immediately recreate the Outlook profile.

---

# 40. Scenario — Outlook Works on Web but Not Desktop

```text
OWA
 ↓
Works

Outlook Desktop
 ↓
Disconnected
```

Focus on:

* Local network
* Authentication state
* Outlook profile
* Office installation
* Cached configuration
* Autodiscover

---

# 41. Scenario — Multiple Users Disconnected

```text
User A → Disconnected
User B → Disconnected
User C → Disconnected
```

Because multiple users are affected, investigate:

```text
Microsoft 365 Service
 ↓
Exchange Online
 ↓
Authentication
 ↓
Network
```

Do not rebuild every user's Outlook profile.

---

# 42. Scenario — Outlook Works on Another Network

```text
Corporate Network
 ↓
Outlook Fails

Home Network
 ↓
Outlook Works
```

Likely investigation areas:

* Proxy
* Firewall
* DNS
* Network filtering
* VPN
* SSL inspection

Escalate to the appropriate network/security team when required.

---

# 43. Scenario — New Profile Fixes Connectivity

```text
Old Profile
 ↓
Connectivity Problem

New Profile
 ↓
Works
```

This provides evidence that the original Outlook profile was likely involved.

Document:

```text
Observed:
Old profile failed.

Validation:
New profile successfully connected.

Conclusion:
Client/profile-level issue.
```

---

# 44. Scenario — Outlook Web and Desktop Both Fail

```text
Outlook Web
 ↓
Fails

Outlook Desktop
 ↓
Fails
```

Investigate:

```text
Account
 ↓
Authentication
 ↓
Conditional Access
 ↓
Microsoft 365
 ↓
Exchange Online
```

Do not start with local Outlook repair.

---

# 45. Support Ticket Example

```text
Issue:
User reported that Outlook repeatedly changed between Connected and Disconnected.

Symptoms:
Email synchronization was intermittent.

Investigation:
Confirmed Internet connectivity.
Tested Outlook Web successfully.
Compared behavior on another network.
Checked Outlook authentication.
Reviewed Outlook profile and client configuration.

Finding:
The issue was isolated to the desktop Outlook/network environment.

Action:
Applied the approved client/network remediation.

Validation:
Outlook remained connected and mail synchronization completed successfully.

Status:
Resolved.
```

---

# 46. Best Practices

### Do

* Start with symptom isolation
* Test Outlook Web
* Check Internet connectivity
* Compare working vs affected environments
* Understand authentication
* Check DNS/network when appropriate
* Check Outlook profile only when justified
* Check service health for widespread issues
* Document evidence
* Escalate with complete troubleshooting information

### Don't

* Immediately recreate Outlook profiles
* Reset passwords without evidence
* Disable MFA
* Disable Conditional Access
* Change DNS without authorization
* Blame Exchange before testing the client
* Blame Outlook before testing the network
* Treat synchronization problems as connectivity problems automatically

---

# 47. Key Takeaways

* Outlook connectivity involves multiple layers.
* "Disconnected" is a symptom, not necessarily the root cause.
* Outlook Web is one of the best isolation tests.
* Network, DNS, authentication, and Outlook profiles can all affect connectivity.
* Cached mailbox synchronization is different from basic connectivity.
* A single-user issue should be approached differently from a widespread outage.
* Comparing working and affected environments is a powerful L2 technique.
* Microsoft 365 service health should be considered when multiple users are affected.
* Troubleshoot from the lowest confirmed failure layer.
* Always document evidence and validation.

---

## Related Documentation

* [Outlook Overview](./01-Outlook-Overview.md)
* [Outlook Configuration](./02-Outlook-Configuration.md)
* [Outlook Profile](./04-Outlook-Profile.md)
* [Outlook Profile Creation](./05-Outlook-Profile-Creation.md)
* [Outlook Profile Corruption](./06-Outlook-Profile-Corruption.md)
* [Shared Mailbox](./17-Shared-Mailbox.md)
* [Distribution Groups](./18-Distribution-Groups.md)
* [Autodiscover](./19-Autodiscover.md)
* [Credential Prompts](./20-Credential-Prompts.md)
* [Outlook Performance](./22-Outlook-Performance.md)
* [Mail Send/Receive Issues](./23-Mail-Send-Receive-Issues.md)
* [Outlook Crash Issues](./24-Outlook-Crash-Issues.md)
* [Real-World Scenarios](./25-Real-World-Scenarios.md)
