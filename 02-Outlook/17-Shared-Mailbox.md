# Outlook Shared Mailbox

## 1. Overview

A **Shared Mailbox** is a Microsoft 365 mailbox designed for multiple users to access a common email address.

Common examples:

- support@company.com
- sales@company.com
- hr@company.com
- info@company.com
- helpdesk@company.com

Instead of assigning a separate user account to every department address, organizations can use a shared mailbox and delegate access to authorized users.

### Conceptual Model

```text
User 1 ─────┐
User 2 ─────┼──────► Shared Mailbox
User 3 ─────┘

Example:

                         ┌─────────────────────┐
User 1 ─────────────────►│                     │
User 2 ─────────────────►│  support@company.com│
User 3 ─────────────────►│                     │
                         │   Shared Mailbox    │
                         └─────────────────────┘
````

### Enterprise Example

```text
                 support@company.com
                         │
                         ▼
              ┌─────────────────────┐
              │    Shared Mailbox    │
              └─────────────────────┘
                    │    │    │
                    ▼    ▼    ▼
                 User 1 User 2 User 3
```



# 2. Why Shared Mailboxes Matter in IT Support

Shared mailbox issues are common in enterprise support.

Users may report:

* Shared mailbox is missing
* Cannot open shared mailbox
* Cannot send from shared mailbox
* Send As is not working
* Send on Behalf is appearing
* Mailbox is not automatically appearing
* Permission was granted but access still fails
* Emails are not appearing
* Sent emails are saved in the wrong location
* User receives an access denied error

A support engineer must understand both **permissions** and **Outlook behavior**.

---


# 3. Shared Mailbox vs User Mailbox

These are different mailbox types.

| Feature                | User Mailbox                                | Shared Mailbox                                    |
| ---------------------- | ------------------------------------------- | ------------------------------------------------- |
| Primary purpose        | Individual user                             | Team / department                                 |
| Login identity         | User account                                | Normally accessed by delegated users              |
| Used by multiple users | Not normally                                | Yes                                               |
| Delegated permissions  | Possible                                    | Core functionality                                |
| Example                | [john@company.com](mailto:john@company.com) | [support@company.com](mailto:support@company.com) |

---


# 4. Example Enterprise Scenario

A company has:

```text
support@company.com
```

Five support engineers need access.

Instead of creating five separate copies of the support mailbox:

```text
Support Engineer 1
Support Engineer 2
Support Engineer 3
Support Engineer 4
Support Engineer 5
```

The organization creates:

```text
support@company.com
        ↓
Shared Mailbox
        ↓
Authorized Support Engineers
```

This provides a central mailbox for the team.

---

# 5. Shared Mailbox Permissions

The most important permissions to understand are:

### Full Access

Allows the user to access and manage mailbox contents.

### Send As

Allows the user to send messages as the shared mailbox.

### Send on Behalf

Allows the user to send messages on behalf of the shared mailbox.

Conceptually:

```text
Full Access
    ↓
Access mailbox

Send As
    ↓
Send as support@company.com

Send on Behalf
    ↓
Send on behalf of support@company.com
```

---

# 6. Full Access

Full Access allows an authorized user to open and work with the shared mailbox.

Typical capabilities include:

* Read email
* Create folders
* Move messages
* Delete messages
* Manage mailbox content

Full Access by itself does **not** automatically mean the user can send as the shared mailbox.

This distinction is important.

---

# 7. Send As

Send As allows a user to send a message where the sender appears to be the shared mailbox.

Example:

```text
From:
support@company.com
```

The recipient generally sees the shared mailbox as the sender.

Conceptually:

```text
User
 ↓
Send As permission
 ↓
support@company.com
 ↓
Recipient
```

---

# 8. Send on Behalf

Send on Behalf allows a user to send a message on behalf of the shared mailbox.

The recipient may see something similar to:

```text
User Name on behalf of support@company.com
```

This is different from Send As.

---

# 9. Send As vs Send on Behalf

| Permission     | Recipient sees                           |
| -------------- | ---------------------------------------- |
| Send As        | Shared mailbox as sender                 |
| Send on Behalf | User sending on behalf of shared mailbox |

Example:

### Send As

```text
From:
support@company.com
```

### Send on Behalf

```text
From:
John on behalf of support@company.com
```

Always confirm the business requirement before assigning either permission.

---

# 10. Creating a Shared Mailbox

A Microsoft 365 administrator can create a shared mailbox through the appropriate Microsoft 365 / Exchange administration interface.

General process:

```text
Admin Center
      ↓
Shared Mailboxes
      ↓
Create Shared Mailbox
      ↓
Name
      ↓
Email Address
      ↓
Create
```

The exact interface can change as Microsoft updates the Microsoft 365 administration experience.

---

# 11. Adding Members

After creating the shared mailbox, authorized users can be assigned access.

Conceptually:

```text
Shared Mailbox
      ↓
Manage Members
      ↓
Add User
      ↓
Assign Required Permissions
```

Follow least-privilege principles.

Only give users the access they actually require.

---

# 12. Assigning Full Access

General workflow:

```text
Shared Mailbox
      ↓
Permissions / Members
      ↓
Full Access
      ↓
Select User
      ↓
Save
```

After permissions propagate, the user may be able to access the mailbox.

---

# 13. Assigning Send As

General workflow:

```text
Shared Mailbox
      ↓
Permissions
      ↓
Send As
      ↓
Add User
      ↓
Save
```

The user can then send messages as the shared mailbox, subject to permission propagation and configuration.

---

# 14. Assigning Send on Behalf

General workflow:

```text
Shared Mailbox
      ↓
Permissions
      ↓
Send on Behalf
      ↓
Add User
      ↓
Save
```

The user can then send messages on behalf of the shared mailbox.

---

# 15. Automapping

Automapping can cause a shared mailbox to automatically appear in Outlook for users who have appropriate access.

Conceptually:

```text
Permission Granted
       ↓
Automapping
       ↓
Outlook
       ↓
Shared Mailbox Appears
```

However, mailbox visibility and Outlook behavior can vary depending on client configuration.

---

# 16. Shared Mailbox Does Not Appear Automatically

### User Report

> "I was given access to the shared mailbox, but it doesn't appear in Outlook."

Troubleshooting:

```text
Confirm Permission
       ↓
Wait for Permission Propagation
       ↓
Restart Outlook
       ↓
Check Outlook Web
       ↓
Check Manual Add
       ↓
Check Profile / Client
```

Do not immediately recreate the entire Outlook profile.

---

# 17. Shared Mailbox Works in Outlook Web

Example:

```text
Outlook Web
      ↓
Shared Mailbox Available

Outlook Desktop
      ↓
Shared Mailbox Missing
```

This is a useful isolation result.

Investigate:

* Outlook Desktop
* Cached configuration
* Profile
* Automapping
* Client state

The mailbox permissions themselves may already be correct.

---

# 18. Shared Mailbox Does Not Work Anywhere

Example:

```text
Outlook Web     → No Access
Outlook Desktop → No Access
```

Investigate:

```text
User Permission
       ↓
Mailbox Configuration
       ↓
Access Assignment
       ↓
Permission Propagation
```

This is more likely to require administrative investigation than a desktop-only issue.

---

# 19. Full Access but Cannot Send

### User Report

> "I can open the shared mailbox but I cannot send email."

Check:

```text
Full Access
     ↓
Can Open Mailbox
```

but:

```text
Send As
     ↓
Required for sending as mailbox
```

Full Access and Send As are separate permissions.

This is one of the most common shared mailbox troubleshooting concepts.

---

# 20. Send As Permission Not Working

### User Report

> "I was given Send As, but Outlook still sends from my personal account."

Check:

```text
Send As Permission
       ↓
Permission Propagation
       ↓
From Address
       ↓
Select Shared Mailbox
```

Also verify that the user is actually selecting the shared mailbox in the **From** field.

---

# 21. Send on Behalf Appears Unexpectedly

### User Report

> "The recipient sees 'John on behalf of [support@company.com](mailto:support@company.com)'."

Possible cause:

The user has Send on Behalf rather than Send As.

Verify the assigned permissions against the business requirement.

If the requirement is:

```text
support@company.com
```

as the visible sender, Send As may be required.

---

# 22. From Field Missing

A user may have access to a shared mailbox but not see the **From** field when composing a message.

General approach:

```text
New Email
      ↓
Enable From Field
      ↓
Select Shared Mailbox
```

The exact Outlook interface varies by client.

---

# 23. Adding the Shared Mailbox Manually

If automapping does not make the mailbox visible, an administrator-supported manual add may be appropriate.

Conceptually:

```text
Outlook
   ↓
Add Shared Mailbox / Account
   ↓
Enter Shared Mailbox Address
   ↓
Confirm
```

The exact steps differ between Outlook versions.

Before manually adding it, verify that the user actually has permission.

---

# 24. Shared Mailbox and Outlook Web

Outlook on the web can be extremely useful for troubleshooting.

Example:

```text
Desktop Problem
       ↓
Test Outlook Web
       ↓
Works
       ↓
Likely Client-Side Issue
```

If it fails in both:

```text
Desktop
   +
Web
   ↓
Investigate Account / Mailbox / Permissions
```

---

# 25. Shared Mailbox and Mail Flow

A shared mailbox can receive messages just like other mail-enabled recipients.

If messages are missing, investigate:

```text
Sender
   ↓
Mail Flow
   ↓
Exchange Online
   ↓
Shared Mailbox
   ↓
Inbox / Other Folder
```

Do not assume a mailbox-access problem is automatically a mail-flow problem.

---

# 26. Shared Mailbox Receiving Email but User Cannot See It

Possible causes include:

* User lacks access
* User is looking at the wrong folder
* Outlook client issue
* Synchronization issue
* Message moved to another folder
* Rule or mailbox processing

Troubleshooting:

```text
Check Mailbox in Outlook Web
        ↓
Locate Message
        ↓
Check Folder
        ↓
Check User Permissions
        ↓
Check Desktop Client
```

---

# 27. Shared Mailbox Sent Items

Organizations may want messages sent from a shared mailbox to be stored in the shared mailbox's Sent Items.

This is an important configuration consideration.

Example:

```text
User sends as:
support@company.com

Expected:
Message saved in
Shared Mailbox → Sent Items
```

If the message instead appears only in the user's personal Sent Items, investigate the organization's shared-mailbox sent-item configuration.

---

# 28. Shared Mailbox Deleted Items

Similar considerations apply to deleted messages.

A user may expect deleted messages to be stored in the shared mailbox's Deleted Items.

If behavior differs, investigate the mailbox configuration and Outlook client behavior.

---

# 29. Shared Mailbox Rules

Shared mailboxes can have mail-processing rules and other configurations.

If emails are unexpectedly moved:

```text
Incoming Email
      ↓
Rule / Processing
      ↓
Folder
```

Investigate rules before assuming the message disappeared.

Related documentation:

[Rules](./08-Rules.md)

---

# 30. Shared Mailbox Permissions and Least Privilege

Follow least privilege.

Example:

```text
User A
 ↓
Read / Access only

User B
 ↓
Full Access + Send As

User C
 ↓
Required business permissions only
```

Do not give Send As or Full Access to users who do not need them.

---

# 31. Shared Mailbox and Licensing

Shared mailbox licensing requirements depend on the mailbox's configuration, size, features, and organizational requirements.

Do not assume:

> "Every shared mailbox is completely free regardless of configuration."

When licensing is involved, verify the organization's Microsoft 365 licensing requirements before making changes.

---

# 32. Shared Mailbox Conversion

In some scenarios, an existing user mailbox may be converted to a shared mailbox.

Conceptually:

```text
User Mailbox
      ↓
Administrative Conversion
      ↓
Shared Mailbox
```

This should be performed only after verifying:

* Business requirement
* User access
* Licensing implications
* Sign-in requirements
* Data requirements
* Organizational policy

---

# 33. Shared Mailbox to User Mailbox

The reverse conversion may also be possible in appropriate administrative scenarios.

Before changing mailbox type, verify:

* Licensing
* Sign-in requirement
* Permissions
* Business ownership
* Mailbox configuration

Do not perform mailbox conversion as a first-line troubleshooting step.

---

# 34. Shared Mailbox and Direct Sign-In

A shared mailbox is normally intended to be accessed through delegated permissions rather than treated as an ordinary user account.

Do not create or use a shared mailbox as a workaround for account-management requirements without following organizational security policy.

---

# 35. Security Considerations

Shared mailboxes can contain sensitive information.

Examples:

* Customer requests
* HR information
* Finance information
* Support tickets
* Internal communications

Therefore:

```text
Shared Mailbox
      ↓
Access Control
      ↓
Authorized Users Only
```

Regularly review membership and permissions according to organizational policy.

---

# 36. Access Review

A good enterprise practice is to periodically review:

```text
Shared Mailbox
      ↓
Members
      ↓
Full Access
      ↓
Send As
      ↓
Send on Behalf
```

Remove access when users no longer require it, following the organization's access-management process.

---

# 37. Scenario — Shared Mailbox Missing

### User Report

> "The support mailbox disappeared from Outlook."

Investigation:

```text
Check Outlook Web
       ↓
Visible?
   /       \
 Yes       No
 ↓          ↓
Desktop    Check Permissions
Issue         ↓
          Check Mailbox
          Configuration
```

If visible on the web, focus on the Outlook client.

---

# 38. Scenario — Full Access Works but Send As Fails

### Incident

```text
Can open mailbox?
YES

Can read emails?
YES

Can send as mailbox?
NO
```

Investigation:

```text
Check Send As
       ↓
Permission Assigned?
       ↓
Wait for Propagation
       ↓
Test From Address
```

Do not remove Full Access simply because Send As is not working.

---

# 39. Scenario — User Sends from Wrong Address

### Incident

> "I thought I sent the email from [support@company.com](mailto:support@company.com), but it went from my personal account."

Check:

```text
New Message
      ↓
From Field
      ↓
Selected Account
```

Then verify Send As permission.

---

# 40. Scenario — Shared Mailbox Works on Web but Not Desktop

### Incident

```text
OWA
 ↓
Shared Mailbox works

Outlook Desktop
 ↓
Missing
```

Investigation:

```text
Check Outlook Profile
       ↓
Check Automapping
       ↓
Restart Outlook
       ↓
Check Manual Add
       ↓
Test
```

Avoid unnecessary mailbox permission changes if the web client already confirms access.

---

# 41. Scenario — User Cannot Access Shared Mailbox

### Incident

```text
Outlook Web
 ↓
Access Denied

Outlook Desktop
 ↓
Access Denied
```

Investigation:

```text
Verify User
     ↓
Verify Shared Mailbox
     ↓
Verify Full Access
     ↓
Check Permission Propagation
     ↓
Test Again
```

Escalate to the appropriate Microsoft 365 administrator when administrative changes are required.

---

# 42. L1 Support Checklist

```text
[ ] Confirm user
[ ] Confirm shared mailbox address
[ ] Confirm expected access
[ ] Check Outlook Web
[ ] Check Outlook Desktop
[ ] Confirm Full Access
[ ] Confirm Send As if required
[ ] Confirm Send on Behalf if required
[ ] Check From field
[ ] Check mailbox folders
[ ] Test sending
[ ] Document result
```

---

# 43. L2 Support Checklist

```text
[ ] Verify mailbox configuration
[ ] Verify permissions
[ ] Verify Full Access
[ ] Verify Send As
[ ] Verify Send on Behalf
[ ] Check permission propagation
[ ] Investigate automapping
[ ] Compare OWA vs Desktop
[ ] Investigate mail flow
[ ] Check sent-item behavior
[ ] Check mailbox rules
[ ] Review licensing requirements
[ ] Validate remediation
[ ] Document root cause
```

---

# 44. Shared Mailbox Troubleshooting Decision Tree

```text
                    Shared Mailbox Issue
                            ↓
                    Does User Have Access?
                       /              \
                     Yes               No
                      ↓                 ↓
              Can Open Mailbox?    Check Permissions
                 /       \                ↓
               Yes        No        Check Propagation
                ↓          ↓              ↓
         Can Send?     Client /      Test Again
          /    \       Permission
        Yes     No
         ↓       ↓
      Check    Check
      From     Send As
      Field    Permission
```

---

# 45. Support Ticket Example

```text
Issue:
User unable to send emails from shared mailbox.

Symptoms:
User can open the shared mailbox and read messages.
User cannot send as the shared mailbox.

Investigation:
Confirmed Full Access.
Verified Send As requirement.
Checked Send As permission.
Validated Outlook From field.

Finding:
User had mailbox access but required sending permission was not correctly configured.

Action:
Correct permission assignment followed by permission propagation.

Validation:
User successfully sent a test message as the shared mailbox.

Status:
Resolved.
```

---

# 46. Best Practices

### Do

* Verify the exact business requirement
* Understand Full Access vs Send As vs Send on Behalf
* Test Outlook Web
* Follow least privilege
* Review shared mailbox membership
* Check permission propagation
* Document mailbox permissions
* Follow organizational licensing and security policies

### Don't

* Give Full Access unnecessarily
* Assume Full Access includes Send As
* Use shared mailboxes as ordinary user accounts
* Change permissions without authorization
* Immediately recreate Outlook profiles
* Assume a missing mailbox is a mail-flow issue
* Ignore Outlook Web during troubleshooting

---

# 47. Key Takeaways

* Shared mailboxes provide a common mailbox for teams and departments.
* Full Access, Send As, and Send on Behalf are different permissions.
* Full Access does not automatically mean Send As.
* Automapping can make shared mailboxes appear automatically in Outlook.
* Outlook Web is an important troubleshooting comparison point.
* Permission propagation can affect newly assigned access.
* Sent-item behavior should be considered when troubleshooting shared mailbox workflows.
* Shared mailbox permissions should follow least privilege.
* Licensing requirements depend on the mailbox configuration and organizational needs.
* Shared mailboxes should be managed according to enterprise security and access policies.

---

## Related Documentation

* [Outlook Overview](./01-Outlook-Overview.md)
* [Outlook Configuration](./02-Outlook-Configuration.md)
* [Outlook Profile](./04-Outlook-Profile.md)
* [Email Management](./07-Email-Management.md)
* [Rules](./08-Rules.md)
* [Search](./14-Search.md)
* [Archive](./15-Archive.md)
* [Distribution Groups](./18-Distribution-Groups.md)
* [Autodiscover](./19-Autodiscover.md)
* [Credential Prompts](./20-Credential-Prompts.md)
* [Mail Send/Receive Issues](./23-Mail-Send-Receive-Issues.md)
* [Real-World Scenarios](./25-Real-World-Scenarios.md)
