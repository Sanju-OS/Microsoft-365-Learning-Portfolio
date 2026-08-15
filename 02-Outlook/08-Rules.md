# Outlook Rules

## 1. Overview

Outlook Rules are automated instructions that process email messages based on defined conditions.

Rules can automatically:

- Move messages
- Copy messages
- Delete messages
- Forward messages
- Categorize messages
- Flag messages
- Mark messages as read
- Apply other supported actions

Rules are useful for email organization, but incorrectly configured rules can also create confusing support incidents.

Example:

```text
Email Received
      ↓
Rule Evaluates Message
      ↓
Condition Matches
      ↓
Action Executes
      ↓
Message Moved / Categorized / Processed
````

---

# 2. Why Rules Matter in Technical Support

Rules are especially important when troubleshooting:

* Missing emails
* Emails moving to unexpected folders
* Automatic forwarding
* Messages being categorized unexpectedly
* Messages being marked as read
* Users receiving unexpected copies
* Mail appearing to disappear from the Inbox

A user may report:

> "The email disappeared."

But the actual cause may be:

```text
Email Received
      ↓
Outlook Rule
      ↓
Message Moved
      ↓
User Cannot Find It
```

Therefore, rules should be included in missing-email troubleshooting.

---

# 3. Rule Components

A typical rule contains:

```text
Condition
   +
Action
   +
Exception
```

For example:

```text
IF
sender = manager@company.com

THEN
move message to "Management"

EXCEPT
subject contains "Urgent"
```

---

# 4. Rule Conditions

Conditions determine when a rule should run.

Examples can include:

* Sender
* Recipient
* Subject
* Keywords
* Message importance
* Message sensitivity
* Specific words
* Messages sent only to the user
* Messages containing attachments

The exact conditions available depend on the Outlook client and organizational environment.

---

# 5. Rule Actions

Actions determine what happens when the conditions match.

Examples include:

* Move message to folder
* Copy message to folder
* Delete message
* Mark as read
* Categorize message
* Flag message
* Forward message
* Redirect message
* Apply other supported Outlook actions

Example:

```text
IF
Subject contains "Invoice"

THEN
Move to "Finance"
```

---

# 6. Rule Exceptions

Exceptions allow specific messages to bypass a rule.

Example:

```text
IF
Subject contains "Report"

THEN
Move to "Reports"

EXCEPT
Sender is CEO
```

This allows more precise automation.

---

# 7. Example Rule

### Requirement

> Move emails from the Finance department into the Finance folder.

Configuration concept:

```text
Condition:
Sender contains finance@company.com

Action:
Move message to Finance folder
```

Result:

```text
Finance Email
     ↓
Rule
     ↓
Finance Folder
```

---

# 8. Creating an Outlook Rule

The exact interface depends on the Outlook version.

The general workflow is:

```text
Open Outlook
    ↓
Settings / Rules
    ↓
Create New Rule
    ↓
Define Condition
    ↓
Define Action
    ↓
Add Exception if Required
    ↓
Save Rule
```

Microsoft provides different Outlook experiences, so the exact menu names can vary.

---

# 9. Rule Example — Manager Emails

### Requirement

> Move messages from my manager to a Management folder.

```text
Condition:
From = manager@company.com

Action:
Move to Management
```

---

# 10. Rule Example — Subject Keyword

### Requirement

> Move emails containing "Invoice" in the subject to Finance.

```text
Condition:
Subject contains "Invoice"

Action:
Move to Finance
```

---

# 11. Rule Example — Customer Emails

### Requirement

> Categorize messages from a customer.

```text
Condition:
Sender = customer@example.com

Action:
Apply "Customer" category
```

This allows the message to remain in the Inbox while being visually identified.

---

# 12. Rule Example — Follow-Up

### Requirement

> Flag messages from a specific sender for follow-up.

```text
Condition:
From = customer@example.com

Action:
Flag for follow-up
```

---

# 13. Rule Example — Important Messages

Rules can be used to prioritize certain messages.

Example:

```text
Condition:
Subject contains "URGENT"

Action:
Apply category "Urgent"
```

Users should still understand that a rule is an organizational aid and not a substitute for proper incident or business-process management.

---

# 14. Rule Ordering

Multiple rules can exist.

Example:

```text
Rule 1 → Finance
Rule 2 → Customers
Rule 3 → Management
Rule 4 → Newsletters
```

The order in which rules are processed can affect the final result.

Therefore, when troubleshooting unexpected email movement, review:

* Which rules exist
* Rule order
* Rule conditions
* Rule actions
* Exceptions
* Whether rule processing stops after a match where applicable

---

# 15. Stop Processing Rules

Some Outlook rule configurations include an option to stop processing additional rules after a rule has matched.

Conceptually:

```text
Rule 1
 ↓
Match
 ↓
Action
 ↓
Stop Further Processing
```

This can prevent later rules from modifying the same message.

Example:

```text
Rule 1:
If sender = CEO
Move to Executive

Stop processing additional rules
```

This prevents subsequent rules from moving the message elsewhere.

---

# 16. Server-Side vs Client-Side Rules

This is an important support concept.

Some rules can be processed by the mail service, while other rules depend on the Outlook client.

Conceptually:

```text
Server-Side Rule
Email
 ↓
Exchange Online
 ↓
Rule
 ↓
Action
```

Client-dependent rule:

```text
Email
 ↓
Exchange Online
 ↓
Mailbox
 ↓
Outlook Client
 ↓
Rule Processing
 ↓
Action
```

The exact behavior depends on the rule and Outlook configuration.

---

# 17. Why Client-Side Rules Matter

A client-dependent rule may not behave as expected when:

* Outlook is closed
* The device is offline
* The Outlook client is not running

This is different from server-side processing.

When troubleshooting rules, determine whether the rule requires the Outlook client.

---

# 18. Rules and Missing Emails

A common support ticket:

> "I received an email, but now I cannot find it."

Troubleshooting:

```text
Search Mailbox
      ↓
Check Inbox
      ↓
Check Deleted Items
      ↓
Check Junk
      ↓
Check Archive
      ↓
Review Rules
      ↓
Check Other Folders
```

If the email is found in an unexpected folder, investigate rules.

---

# 19. Scenario — Email Automatically Moves

### User Report

> "Every email from my manager disappears from my Inbox."

### Investigation

Search the mailbox.

The message is found in:

```text
Management
```

Review Outlook Rules.

A rule is found:

```text
IF sender = manager@company.com
THEN move to Management
```

### Resolution

Explain the rule to the user and modify or remove it according to the user's requirement and organizational procedures.

### Validation

Send a test email and confirm that the message appears in the expected location.

---

# 20. Scenario — Rule Causes Multiple Actions

### Problem

A message is:

1. Moved to a folder
2. Categorized
3. Forwarded

### Investigation

Review all active rules.

Example:

```text
Rule 1
 ↓
Move to Folder

Rule 2
 ↓
Apply Category

Rule 3
 ↓
Forward
```

The unexpected behavior may be caused by multiple rules rather than one incorrect rule.

---

# 21. Scenario — Email Is Automatically Forwarded

Automatic forwarding deserves special attention because it can have security implications.

Investigate:

* Outlook rules
* Mailbox forwarding configuration
* Organizational policies
* Security controls
* Whether the forwarding destination is internal or external

Do not assume that forwarding was intentionally configured by the user.

Unexpected external forwarding should be treated as a potential security concern and handled according to organizational incident-response procedures.

---

# 22. Scenario — Rule Works for One User but Not Another

Possible differences include:

* Rule configuration
* Outlook client
* Mailbox configuration
* Permissions
* Organizational policies
* Rule processing location
* Different Outlook experiences

Compare:

```text
User A
 ↓
Rules
 ↓
Configuration

User B
 ↓
Rules
 ↓
Configuration
```

Do not assume that identical business requirements mean identical technical configurations.

---

# 23. Troubleshooting Rules

When investigating unexpected rule behavior:

### Step 1 — Identify the affected message

Collect:

* Sender
* Recipient
* Subject
* Date/time
* Expected location
* Actual location

### Step 2 — Search the mailbox

Determine where the message actually exists.

### Step 3 — Review Rules

Check:

* Active rules
* Conditions
* Actions
* Exceptions
* Rule order

### Step 4 — Test

Send a controlled test message.

### Step 5 — Modify One Thing

Avoid changing many rules simultaneously.

### Step 6 — Validate

Confirm the message is processed as expected.

---

# 24. Rule Troubleshooting Decision Tree

```text
Email Not Where Expected
          ↓
Search Mailbox
          ↓
Message Found?
       /       \
     Yes        No
      ↓          ↓
Check Folder   Check Deleted
      ↓        / Junk / Archive
Check Rules        ↓
      ↓         Mail Flow
Rule Found?
   /     \
 Yes      No
  ↓        ↓
Review    Investigate
Rule      Mail Flow /
          Client / Service
```

---

# 25. Rule Documentation

For enterprise support, document rules clearly.

Example:

```text
Rule Name:
Finance Emails

Condition:
Sender contains finance@company.com

Action:
Move to Finance folder

Exception:
Subject contains "Urgent"

Status:
Enabled

Purpose:
Organize Finance communications
```

This makes future troubleshooting easier.

---

# 26. Security Considerations

Rules can be abused to hide or forward messages.

Unexpected rules may indicate:

* Accidental configuration
* User misconfiguration
* Compromised account
* Unauthorized forwarding

If a user reports unexpected forwarding or suspicious rule creation:

```text
Suspicious Rule
      ↓
Preserve Evidence
      ↓
Verify User
      ↓
Review Account Activity
      ↓
Follow Security Incident Process
```

Do not simply delete suspicious configuration without following organizational procedures where incident investigation is required.

---

# 27. L1 Support Checklist

```text
[ ] Confirm affected user
[ ] Identify missing/unexpected email
[ ] Search mailbox
[ ] Identify actual message location
[ ] Review Outlook Rules
[ ] Check rule conditions
[ ] Check rule actions
[ ] Check exceptions
[ ] Check rule order
[ ] Test with controlled email
[ ] Document result
[ ] Escalate suspicious activity
```

---

# 28. L2 Support Checklist

```text
[ ] Determine scope
[ ] Review all applicable rules
[ ] Analyze rule processing
[ ] Determine client/server behavior
[ ] Investigate forwarding
[ ] Check mailbox configuration
[ ] Check organizational policies
[ ] Investigate security implications
[ ] Validate remediation
[ ] Document root cause
```

---

# 29. Best Practices

### Do

* Use clear rule names
* Keep rules simple
* Review rule order
* Use exceptions when necessary
* Test new rules
* Document important rules
* Review unexpected forwarding carefully

### Don't

* Create unnecessary duplicate rules
* Create overly complicated rule chains
* Delete suspicious rules without considering security procedures
* Assume missing email means mail-flow failure
* Modify many rules simultaneously during troubleshooting

---

# 30. Real-World L2 Scenario

### Incident

> User reports that customer emails are automatically moved out of the Inbox.

### Investigation

```text
User
 ↓
Search mailbox
 ↓
Message found in Customer folder
 ↓
Review Rules
 ↓
Rule identified
 ↓
Review condition
 ↓
Review action
 ↓
Test
```

### Finding

The rule:

```text
IF sender contains customer-domain.com
THEN move to Customer folder
```

was intentionally configured previously.

### Resolution

The rule is modified according to the user's current business requirement.

### Validation

A test customer email is sent and confirmed to remain in the desired folder.

### Documentation

```text
Symptom:
Customer emails not visible in Inbox

Cause:
Outlook rule moved messages

Action:
Updated rule

Validation:
Test message confirmed correct behavior
```

---

# 31. Key Takeaways

* Outlook Rules automate email processing.
* Rules contain conditions, actions, and optional exceptions.
* Multiple rules can interact with each other.
* Rule order can affect behavior.
* Some rules may depend on the Outlook client.
* Rules are a common cause of "missing email" incidents.
* Unexpected forwarding should be investigated carefully.
* Suspicious rules may represent a security concern.
* Always test rule changes with controlled messages.
* L2 support should document the rule, cause, action, and validation.

---

## Related Documentation

* [Email Management](./07-Email-Management.md)
* [Signatures](./09-Signatures.md)
* [Automatic Replies](./10-Automatic-Replies.md)
* [Search](./14-Search.md)
* [Archive](./15-Archive.md)
* [PST Files](./16-PST-Files.md)
* [Shared Mailbox](./17-Shared-Mailbox.md)
* [Credential Prompts](./20-Credential-Prompts.md)
* [Mail Send/Receive Issues](./23-Mail-Send-Receive-Issues.md)
* [Real-World Scenarios](./25-Real-World-Scenarios.md)
