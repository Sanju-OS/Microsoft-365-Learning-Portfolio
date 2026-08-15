# Outlook Mail Send/Receive Issues

## 1. Overview

Microsoft Outlook depends on Exchange Online and Microsoft 365 services to send and receive email.

A simplified mail flow is:

```text
User
 ↓
Outlook
 ↓
Authentication
 ↓
Exchange Online
 ↓
Microsoft 365 Mail Flow
 ↓
Recipient Mailbox
````

When a user reports that email is not sending or receiving, first determine **where the failure occurs**.

---

# 2. Common Symptoms

Users may report:

* Email stuck in Outbox
* Email not sending
* Email not receiving
* Delayed email
* Send/Receive error
* Emails disappearing
* Emails going to Junk
* Emails going to the wrong folder
* NDR / bounce-back message
* Large attachment cannot be sent
* External emails not arriving
* Internal emails not arriving
* Outlook shows Disconnected
* Outlook Web works but Desktop does not

---

# 3. Send vs Receive

Always determine whether the issue affects:

```text
Send
Receive
Both
```

Example:

```text
Send → Works
Receive → Fails
```

This requires a different investigation from:

```text
Send → Fails
Receive → Works
```

---

# 4. First Troubleshooting Questions

Ask the user:

1. Can you send email?
2. Can you receive email?
3. Does the problem affect internal email?
4. Does the problem affect external email?
5. Is the email stuck in Outbox?
6. Do you receive an error?
7. Can you use Outlook Web successfully?
8. When did the problem start?
9. Is the issue affecting other users?
10. Did anything recently change?

---

# 5. Test Outlook Web

Outlook Web is an important isolation test.

```text
Outlook Web
      ↓
Send Test Email
      ↓
Receive Test Email
```

Compare the result with Outlook Desktop.

---

# 6. Outlook Web Works, Desktop Fails

Example:

```text
Outlook Web
 ↓
Send/Receive Works

Outlook Desktop
 ↓
Fails
```

Focus on:

* Outlook connectivity
* Outlook profile
* Authentication
* Cached data
* Local configuration
* Add-ins
* Network

Related documentation:

[Outlook Connectivity](./21-Outlook-Connectivity.md)

---

# 7. Outlook Web Also Fails

Example:

```text
Outlook Web
 ↓
Send/Receive Fails

Outlook Desktop
 ↓
Fails
```

Investigate broader areas:

```text
Account
 ↓
Exchange Online
 ↓
Mailbox
 ↓
Mail Flow
 ↓
Microsoft 365 Service
```

---

# 8. Email Stuck in Outbox

### User Report

> "My email is stuck in the Outbox."

Possible causes:

* Outlook disconnected
* Network issue
* Authentication problem
* Large attachment
* Corrupted message
* Outlook profile problem
* Mail flow issue
* Service issue

Start with:

```text
Outbox
 ↓
Outlook Connection
 ↓
Authentication
 ↓
Attachment
 ↓
Exchange Online
```

---

# 9. Check Outlook Connection

If an email remains in Outbox, check Outlook status.

Example:

```text
Outlook
 ↓
Disconnected
 ↓
Email remains in Outbox
```

If Outlook is disconnected, troubleshoot connectivity first.

See:

[Outlook Connectivity](./21-Outlook-Connectivity.md)

---

# 10. Large Attachment

A large attachment may delay or prevent sending.

Example:

```text
Email
 +
Large Attachment
 ↓
Upload
 ↓
Send
```

Check:

* Attachment size
* Organization limits
* Recipient limits
* Network stability

Do not assume every failed attachment is an Outlook problem.

---

# 11. Remove Attachment as a Test

A useful isolation test:

```text
Email + Attachment
 ↓
Fails

Same Email Without Attachment
 ↓
Works
```

This suggests investigating the attachment or size limitation.

---

# 12. Test a New Email

If one email is stuck:

```text
Existing Email
 ↓
Stuck

New Test Email
 ↓
Works
```

The original message may be the problem.

Possible causes:

* Attachment
* Message corruption
* Embedded content
* Add-in
* Formatting

---

# 13. Send Test Email Internally

Send:

```text
User A
 ↓
User B
```

If successful:

```text
Internal Send → Works
```

Then test external sending separately.

---

# 14. Send Test Email Externally

Example:

```text
User
 ↓
Exchange Online
 ↓
External Recipient
```

If internal email works but external email fails, investigate:

* Mail flow
* Outbound restrictions
* Transport rules
* Recipient domain
* Security controls
* External recipient rejection

---

# 15. Receive Test Email Internally

Ask another internal user to send:

```text
User B
 ↓
User A
```

If it does not arrive, investigate:

* Mailbox
* Rules
* Junk
* Quarantine
* Mail flow
* Exchange Online

---

# 16. Receive Test Email Externally

Test:

```text
External Sender
 ↓
Microsoft 365
 ↓
User Mailbox
```

If internal email arrives but external email does not, investigate external mail flow.

---

# 17. Internal vs External Troubleshooting

Use this matrix:

| Test             | Result | Direction         |
| ---------------- | ------ | ----------------- |
| Internal Send    | Works  | Outbound internal |
| External Send    | Fails  | Outbound external |
| Internal Receive | Works  | Inbound internal  |
| External Receive | Fails  | Inbound external  |

This helps narrow the issue.

---

# 18. Email Not Receiving

Possible causes:

* Outlook disconnected
* Mailbox issue
* Inbox rule
* Junk Email
* Quarantine
* Mail flow rule
* Sender issue
* Recipient address issue
* Service issue

First check whether the email exists somewhere else.

---

# 19. Check Junk Email

If a user says:

> "I didn't receive the email."

Check:

```text
Inbox
 ↓
Junk Email
 ↓
Deleted Items
 ↓
Other Folders
```

Do not immediately conclude that the email was never delivered.

---

# 20. Check Inbox Rules

Rules can automatically move messages.

Example:

```text
Incoming Email
      ↓
Inbox Rule
      ↓
Specific Folder
```

A user may think an email is missing when it was moved by a rule.

See:

[Rules](./08-Rules.md)

---

# 21. Focused Inbox / Other

Depending on the Outlook experience, messages may appear in different views.

Check:

* Focused
* Other
* Junk
* Archive
* Deleted Items
* Custom folders

Search can also help locate the message.

See:

[Search](./14-Search.md)

---

# 22. Search for Missing Email

If the user cannot find an email:

```text
Search
 ↓
Sender
 ↓
Subject
 ↓
Date
 ↓
Recipient
```

Do not assume the message was deleted.

---

# 23. Email Delay

A user may report:

> "The email arrived 30 minutes late."

Determine where the delay occurred.

```text
Sender
 ↓
Sender Mail System
 ↓
Exchange Online
 ↓
Mail Flow
 ↓
Recipient Mailbox
 ↓
Outlook
```

The delay may occur at any stage.

---

# 24. Outlook Delay vs Mail Flow Delay

Important distinction:

### Outlook Delay

Email exists in the mailbox but Outlook Desktop has not synchronized it.

### Mail Flow Delay

Email has not reached the mailbox yet.

Compare:

```text
Outlook Web
      vs
Outlook Desktop
```

If Web already has the email but Desktop does not:

```text
Mailbox → Works
Outlook Sync → Investigate
```

---

# 25. Outlook Web Has Email, Desktop Does Not

Example:

```text
Outlook Web
 ↓
Email visible

Outlook Desktop
 ↓
Email missing
```

Investigate:

* Outlook connectivity
* Cached mailbox
* Synchronization
* Outlook profile
* Local client

---

# 26. Neither Web nor Desktop Has Email

Example:

```text
Outlook Web
 ↓
Missing

Outlook Desktop
 ↓
Missing
```

Investigate:

```text
Sender
 ↓
Mail Flow
 ↓
Exchange Online
 ↓
Mailbox
```

This is less likely to be a simple Outlook desktop issue.

---

# 27. NDR / Bounce-Back

NDR means:

**Non-Delivery Report**

A user may receive an email explaining why delivery failed.

Example:

```text
Sender
 ↓
Exchange Online
 ↓
Delivery Attempt
 ↓
Failure
 ↓
NDR
```

The NDR contains useful diagnostic information.

---

# 28. Read the NDR Carefully

Look for:

* Recipient address
* Error code
* SMTP response
* Delivery status
* Remote server
* Reason for rejection

Do not simply forward an NDR without analyzing it.

---

# 29. Common NDR Categories

Possible categories include:

* Invalid recipient
* Mailbox unavailable
* Mailbox full
* Message too large
* Sender blocked
* Recipient blocked
* Authentication/restriction
* Transport rule
* Remote server rejection
* Domain configuration issue

---

# 30. Invalid Recipient

Example:

```text
User sends to:
someone@company.com

Recipient address incorrect
        ↓
Delivery Failure
        ↓
NDR
```

Verify the recipient address.

---

# 31. Mailbox Full

A recipient mailbox may be unable to receive additional messages because of applicable storage or service limits.

Investigation:

```text
Sender
 ↓
Recipient
 ↓
Mailbox Capacity
 ↓
Delivery Result
```

Follow organizational Microsoft 365 procedures before changing mailbox settings.

---

# 32. Message Too Large

Example:

```text
Email
 ↓
Large Attachment
 ↓
Size Limit
 ↓
NDR
```

Check:

* Message size
* Attachment size
* Organization limits
* Recipient system limits

---

# 33. External Recipient Rejects Message

Example:

```text
Microsoft 365
 ↓
External Mail Server
 ↓
Rejects Message
 ↓
NDR
```

The external recipient's mail server may be responsible for the rejection.

Review the SMTP response and NDR details.

---

# 34. Sender Blocked

A message may be rejected because of:

* Sender restrictions
* Security policies
* Recipient restrictions
* Spam controls
* Organization configuration

Do not bypass security controls simply to make a message deliver.

---

# 35. Mail Flow

Mail flow describes how email moves through the messaging environment.

Simplified:

```text
Sender
 ↓
Exchange Online
 ↓
Mail Flow Processing
 ↓
Recipient
```

Mail flow processing can involve:

* Anti-spam
* Anti-malware
* Transport rules
* Connectors
* DLP
* Security policies

---

# 36. Transport Rules

Transport rules can modify or reject messages.

Example:

```text
Incoming Message
       ↓
Transport Rule
       ↓
Action
       ↓
Deliver / Modify / Reject
```

Possible actions depend on the organization's configuration.

Support engineers should understand the rule before making changes.

---

# 37. Mail Flow vs Outlook

Important distinction:

```text
Outlook
 ↓
Email Successfully Sent
 ↓
Exchange Online
 ↓
Mail Flow
 ↓
Recipient
```

If Outlook successfully submits the email but delivery fails later, the problem may be in mail flow rather than the Outlook client.

---

# 38. Authentication and Sending

If Outlook cannot authenticate:

```text
Authentication Failure
       ↓
Exchange Connection
       ↓
Send/Receive Failure
```

Check:

* Outlook status
* Microsoft 365 login
* MFA
* Conditional Access
* Credential prompts

Related documentation:

[Credential Prompts](./20-Credential-Prompts.md)

---

# 39. Send/Receive Error

If Outlook displays a Send/Receive error:

Capture:

```text
Error Message
Error Code
Time
Affected Account
```

Then determine:

```text
Client
 ↓
Network
 ↓
Authentication
 ↓
Exchange Online
 ↓
Mail Flow
```

---

# 40. Outlook Offline

If Outlook is in Offline mode:

```text
Working Offline
 ↓
Mail May Not Synchronize
```

Verify whether offline mode was intentionally enabled.

If not, investigate connectivity.

---

# 41. Outlook Connectivity Relationship

```text
Internet
 ↓
Authentication
 ↓
Outlook
 ↓
Exchange Online
 ↓
Mailbox
```

A connectivity problem can affect both sending and receiving.

See:

[Outlook Connectivity](./21-Outlook-Connectivity.md)

---

# 42. Outlook Rules and Send/Receive

Rules can affect how messages appear to users.

Example:

```text
Incoming Email
 ↓
Rule
 ↓
Move / Categorize / Delete / Forward
```

When investigating missing email, check rules before concluding that the message was lost.

---

# 43. Automatic Replies

Automatic replies are configured at the mailbox/service level and can affect how users perceive incoming/outgoing messages.

Verify:

* Automatic Replies status
* Start/end dates
* Internal message
* External message

See:

[Automatic Replies](./10-Automatic-Replies.md)

---

# 44. Shared Mailbox Send Issue

A user may be unable to send from a shared mailbox.

Possible areas:

```text
User
 ↓
Shared Mailbox
 ↓
Permissions
 ↓
Send As / Send on Behalf
 ↓
Exchange Online
```

Verify that the user has the required permission.

See:

[Shared Mailbox](./17-Shared-Mailbox.md)

---

# 45. Distribution Group Send Issue

If sending to a distribution group fails:

Check:

* Correct group address
* Sender permissions
* Group restrictions
* Message size
* Mail flow rules
* External sender restrictions

Do not assume the Outlook client is the problem.

See:

[Distribution Groups](./18-Distribution-Groups.md)

---

# 46. Email Disappears After Sending

Possible locations:

```text
Sent Items
 ↓
Deleted Items
 ↓
Archive
 ↓
Other Folder
```

Also investigate:

* Rules
* Retention
* Mailbox policies
* Delegation
* Shared mailbox behavior

---

# 47. Email Goes to Junk

If messages are being delivered to Junk:

```text
Sender
 ↓
Exchange Online
 ↓
Security Filtering
 ↓
Junk
```

Investigate:

* Sender
* Recipient
* Message characteristics
* Organization security controls
* Safe/blocked sender configuration

Do not weaken spam protection without authorization.

---

# 48. External Email Not Received

### Scenario

> "Internal email works, but Gmail/external email never arrives."

Test:

```text
Internal Sender
 ↓
Works

External Sender
 ↓
Fails
```

Investigate:

```text
External Sender
 ↓
Internet Mail
 ↓
Microsoft 365
 ↓
Security Filtering
 ↓
Mailbox
```

---

# 49. Internal Email Not Received

If internal mail also fails:

```text
User A
 ↓
Microsoft 365
 ↓
User B
```

Investigate:

* Mailbox
* Exchange Online
* Recipient address
* Rules
* Service health
* Mail flow

---

# 50. Both Send and Receive Fail

If both directions fail:

```text
Send → Fail
Receive → Fail
```

Prioritize:

```text
Connectivity
 ↓
Authentication
 ↓
Account
 ↓
Exchange Online
 ↓
Service Health
```

---

# 51. Only Send Fails

If:

```text
Send → Fail
Receive → Works
```

Investigate:

* Outbox
* Attachment
* Send permissions
* Mail flow
* Recipient
* NDR
* Transport restrictions

---

# 52. Only Receive Fails

If:

```text
Send → Works
Receive → Fails
```

Investigate:

* Mailbox
* Inbox rules
* Junk
* Quarantine
* Mail flow
* Sender
* Synchronization

---

# 53. L1 Troubleshooting Checklist

```text
[ ] Confirm Send / Receive / Both
[ ] Capture exact error
[ ] Check Outlook connection
[ ] Test Outlook Web
[ ] Send internal test
[ ] Send external test
[ ] Receive internal test
[ ] Receive external test
[ ] Check Outbox
[ ] Check Junk
[ ] Check Inbox rules
[ ] Search mailbox
[ ] Check NDR
[ ] Document findings
```

---

# 54. L2 Troubleshooting Checklist

```text
[ ] Check Exchange Online
[ ] Check Microsoft 365 service health
[ ] Analyze NDR
[ ] Investigate mail flow
[ ] Review transport rules
[ ] Check connectors where applicable
[ ] Check mailbox configuration
[ ] Check shared mailbox permissions
[ ] Check distribution group restrictions
[ ] Check authentication
[ ] Check Conditional Access where applicable
[ ] Validate resolution
[ ] Document root cause
```

---

# 55. Mail Troubleshooting Decision Tree

```text
                  Email Problem
                       ↓
             Send or Receive?
                /           \
              Send         Receive
               ↓             ↓
        Check Outbox     Check Inbox
               ↓             ↓
        Outlook Connected?  Search/Junk
               ↓             ↓
        Test Outlook Web   Check Rules
               ↓             ↓
        Internal Test      Internal Test
               ↓             ↓
        External Test      External Test
               ↓             ↓
          NDR/Mail Flow    Mail Flow
```

---

# 56. Scenario — Email Stuck in Outbox

```text
Issue:
User cannot send an email.

Investigation:
Confirmed Outlook was connected.
Checked the message size.
Tested a new email without the attachment.
New email sent successfully.

Finding:
The original message/attachment was contributing to the issue.

Action:
Applied the approved remediation and resent the message.

Validation:
Email successfully reached the recipient.
```

---

# 57. Scenario — Internal Works, External Fails

```text
Issue:
User can send email internally but not externally.

Investigation:
Internal test succeeded.
External test failed.
Reviewed NDR.
Investigated outbound mail flow and applicable restrictions.

Finding:
Issue was isolated to external delivery rather than the Outlook client.

Action:
Escalated/updated the appropriate mail-flow configuration according to organizational procedure.

Validation:
External test email was delivered successfully.
```

---

# 58. Scenario — Outlook Desktop Does Not Receive Email

```text
Issue:
User cannot see new emails in Outlook Desktop.

Investigation:
Outlook Web showed the new messages.
Outlook Desktop did not.

Finding:
Mailbox delivery was working.
Problem was isolated to Outlook synchronization/client.

Action:
Investigated Outlook connectivity, cached data, and profile.

Validation:
Desktop Outlook synchronized successfully.
```

---

# 59. Scenario — NDR Received

```text
Issue:
User received a non-delivery report.

Investigation:
Reviewed recipient address.
Reviewed SMTP response.
Reviewed delivery status.
Determined whether failure occurred locally or at the recipient domain.

Finding:
Delivery was rejected during mail flow.

Action:
Followed the applicable mail-flow remediation/escalation procedure.

Validation:
A subsequent test message was delivered successfully.
```

---

# 60. Support Ticket Template

```text
Issue:
[Describe the user's email problem]

Symptoms:
[Describe exact behavior]

Scope:
[One user / multiple users]

Send:
[Works / Fails]

Receive:
[Works / Fails]

Internal Email:
[Works / Fails]

External Email:
[Works / Fails]

Outlook Web:
[Works / Fails]

Outlook Desktop:
[Works / Fails]

Error / NDR:
[Record relevant error]

Investigation:
[List troubleshooting performed]

Root Cause:
[Document confirmed cause]

Resolution:
[Document approved remediation]

Validation:
[Explain how the fix was confirmed]

Status:
[Resolved / Escalated]
```

---

# 61. Best Practices

### Do

* Separate send and receive troubleshooting.
* Test internal and external mail.
* Test Outlook Web.
* Analyze NDR messages.
* Check Outbox.
* Check Junk and mailbox rules.
* Understand mail flow.
* Check connectivity.
* Check service health when appropriate.
* Document evidence and validation.

### Don't

* Immediately reinstall Outlook.
* Immediately recreate the profile.
* Delete emails as a troubleshooting step.
* Disable spam/security controls without authorization.
* Ignore NDR information.
* Assume every delivery issue is caused by Outlook.
* Assume every Outlook issue is caused by Exchange Online.

---

# 62. Key Takeaways

* Always determine whether the issue affects sending, receiving, or both.
* Internal and external mail testing helps isolate mail-flow problems.
* Outlook Web is useful for separating desktop issues from mailbox/service issues.
* An NDR contains valuable diagnostic information.
* Emails can be delivered but hidden by rules, Junk, or other mailbox organization.
* An email stuck in Outbox can be caused by connectivity, attachment, authentication, or client issues.
* Successful Outlook submission does not guarantee successful final delivery.
* Mail flow and Outlook client troubleshooting are different layers.
* L2 support should identify the failure point before applying remediation.
* Always document the root cause and validation.

---

## Related Documentation

* [Outlook Overview](./01-Outlook-Overview.md)
* [Email Management](./07-Email-Management.md)
* [Rules](./08-Rules.md)
* [Automatic Replies](./10-Automatic-Replies.md)
* [Search](./14-Search.md)
* [Shared Mailbox](./17-Shared-Mailbox.md)
* [Distribution Groups](./18-Distribution-Groups.md)
* [Credential Prompts](./20-Credential-Prompts.md)
* [Outlook Connectivity](./21-Outlook-Connectivity.md)
* [Outlook Performance](./22-Outlook-Performance.md)
* [Real-World Scenarios](./25-Real-World-Scenarios.md)
