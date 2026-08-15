# Outlook Autodiscover

## 1. Overview

**Autodiscover** is an Exchange feature that helps Outlook automatically discover the configuration required to connect a user's mailbox.

Instead of manually entering every Exchange connection setting, Outlook uses the user's email identity and Autodiscover information to determine the appropriate mailbox configuration.

Simplified:

```text
User Email Address
        ↓
Outlook
        ↓
Autodiscover
        ↓
Exchange Online
        ↓
Mailbox Configuration
        ↓
Outlook Connects
````

Autodiscover is especially important when troubleshooting:

* Outlook profile creation
* Outlook connectivity
* Authentication
* Mailbox configuration
* Exchange Online connectivity
* Credential prompts
* New-user setup

---

# 2. Why Autodiscover Matters

When a user enters:

```text
user@company.com
```

Outlook needs to discover information about the user's mailbox and Exchange environment.

Autodiscover helps Outlook obtain the required configuration automatically.

Without working Autodiscover, users may experience:

* Outlook unable to configure an account
* Repeated password prompts
* Outlook disconnected
* Incorrect mailbox configuration
* Profile creation failures
* Calendar or free/busy problems
* Mailbox connectivity issues

---

# 3. Autodiscover and Microsoft 365

In a Microsoft 365 environment, Outlook commonly uses the organization's Microsoft 365 domain and Exchange Online service to discover mailbox configuration.

Conceptually:

```text
user@company.com
       ↓
company.com
       ↓
Autodiscover
       ↓
Microsoft 365 / Exchange Online
       ↓
User Mailbox
```

The exact discovery process depends on the Outlook client and environment.

---

# 4. Autodiscover Architecture

A simplified architecture is:

```text
                Internet
                   ↓
             DNS / Identity
                   ↓
              Autodiscover
                   ↓
            Exchange Online
                   ↓
              Mailbox
                   ↓
               Outlook
```

In hybrid or on-premises environments, the architecture can be more complex.

---

# 5. Autodiscover in a New Outlook Profile

When creating an Outlook profile:

```text
User enters email
       ↓
Outlook starts discovery
       ↓
Autodiscover request
       ↓
Mailbox configuration discovered
       ↓
Authentication
       ↓
Profile configured
```

This is why Autodiscover problems can appear as **profile creation problems**.

---

# 6. Autodiscover and DNS

DNS is an important component of Autodiscover troubleshooting.

Organizations may use an Autodiscover DNS record for their email domain.

Conceptually:

```text
autodiscover.company.com
          ↓
DNS
          ↓
Microsoft 365 / Exchange environment
```

The exact DNS configuration depends on the organization's Microsoft 365 architecture.

---

# 7. Autodiscover DNS Record

A common Autodiscover configuration uses a DNS record such as:

```text
autodiscover.company.com
```

The record must point to the appropriate service according to Microsoft's supported configuration for the organization's environment.

When troubleshooting DNS, verify the actual record rather than assuming its target.

---

# 8. Autodiscover and HTTPS

Autodiscover communication uses secure HTTPS-based communication.

Simplified:

```text
Outlook
   ↓
HTTPS
   ↓
Autodiscover Service
   ↓
Mailbox Configuration
```

Therefore, certificate and network issues can affect Autodiscover in some environments.

---

# 9. Autodiscover and Authentication

Autodiscover is not simply a DNS lookup.

The overall process may involve:

```text
DNS
 ↓
Autodiscover
 ↓
Authentication
 ↓
Exchange Online
 ↓
Mailbox Configuration
```

Authentication problems can therefore appear to users as Autodiscover problems.

---

# 10. Autodiscover and Microsoft Entra ID

Modern Microsoft 365 authentication can involve Microsoft Entra ID.

Conceptually:

```text
Outlook
   ↓
Microsoft 365
   ↓
Microsoft Entra ID
   ↓
Authentication
   ↓
Exchange Online
```

Therefore, an Autodiscover-related Outlook problem may actually involve:

* Account authentication
* MFA
* Conditional Access
* Token issues
* Identity configuration

---

# 11. Autodiscover vs Mailbox Connectivity

These are related but different.

### Autodiscover

Helps Outlook discover mailbox configuration.

### Mailbox Connectivity

Allows Outlook to communicate with Exchange after configuration.

Conceptually:

```text
Autodiscover
     ↓
Find Configuration
     ↓
Exchange Connection
     ↓
Mailbox Access
```

If Autodiscover succeeds but Outlook cannot connect, investigate the connectivity layer separately.

---

# 12. Autodiscover vs Outlook Profile

An Outlook profile contains account and configuration information used by Outlook.

Autodiscover can provide information required when creating or configuring the profile.

Therefore:

```text
Autodiscover
      ↓
Mailbox Configuration
      ↓
Outlook Profile
      ↓
Exchange Connection
```

A corrupted profile can also create symptoms that look like Autodiscover problems.

---

# 13. Common Autodiscover Problems

Common scenarios include:

1. Outlook cannot configure account
2. Autodiscover fails
3. Incorrect DNS configuration
4. Authentication failure
5. Repeated credential prompts
6. Outlook connects to the wrong account
7. Outlook profile creation fails
8. Hybrid configuration problems
9. Network/proxy interference
10. Certificate problems

---

# 14. Scenario — Outlook Cannot Configure Account

### User Report

> "Outlook cannot automatically set up my Microsoft 365 account."

Start with:

```text
Email Address
     ↓
Internet Connectivity
     ↓
Microsoft 365 Sign-In
     ↓
Autodiscover
     ↓
Exchange Online
```

Do not immediately recreate the profile.

First determine where the failure occurs.

---

# 15. Basic Autodiscover Troubleshooting

Use this workflow:

```text
1. Confirm email address
        ↓
2. Confirm Internet connectivity
        ↓
3. Test Microsoft 365 sign-in
        ↓
4. Test Outlook Web
        ↓
5. Check DNS
        ↓
6. Test Autodiscover
        ↓
7. Check authentication
        ↓
8. Check Outlook profile
```

---

# 16. Test Outlook Web

Outlook Web is useful for isolating the problem.

Example:

```text
Outlook Web
     ↓
Can user sign in?
```

### If yes

The account and mailbox may be functioning, so investigate the Outlook desktop client.

### If no

Investigate:

* Identity
* Authentication
* Account status
* Service availability
* Conditional Access

---

# 17. Outlook Web Works but Outlook Desktop Does Not

Example:

```text
Outlook Web
     ↓
Works

Outlook Desktop
     ↓
Fails
```

This suggests investigating:

* Outlook profile
* Cached credentials
* Autodiscover
* Local configuration
* Office installation
* Network/proxy configuration

---

# 18. Outlook Web Also Fails

Example:

```text
Outlook Web
     ↓
Fails

Outlook Desktop
     ↓
Fails
```

Do not focus only on the local Outlook client.

Investigate:

```text
Account
 ↓
Authentication
 ↓
Microsoft 365 Service
 ↓
Mailbox
```

---

# 19. Credential Prompt During Autodiscover

### User Report

> "Outlook keeps asking for my password."

Possible areas:

```text
Identity
 ↓
Authentication
 ↓
Autodiscover
 ↓
Outlook Profile
 ↓
Credential Cache
```

Credential prompts are not always caused by a wrong password.

Related documentation:

[Credential Prompts](./20-Credential-Prompts.md)

---

# 20. Incorrect Credentials

Before changing anything, verify:

* User account
* Email address
* Password
* Account status
* MFA requirement
* Authentication method

Do not ask users to repeatedly enter credentials without identifying why authentication is failing.

---

# 21. Autodiscover and MFA

Modern Microsoft 365 environments may use MFA.

The authentication sequence can involve:

```text
Outlook
   ↓
Microsoft 365 Authentication
   ↓
MFA
   ↓
Authentication Token
   ↓
Exchange Online
```

If authentication succeeds in the browser but Outlook fails, investigate the Outlook client and authentication state.

---

# 22. Autodiscover and Conditional Access

Conditional Access policies can affect authentication.

Example:

```text
Outlook
   ↓
Authentication Request
   ↓
Conditional Access
   ↓
Access Evaluation
   ↓
Allow / Block / Require Control
```

If a user is blocked by Conditional Access, the issue may appear to the user as an Outlook sign-in or connectivity problem.

Do not modify Conditional Access policies without authorization.

---

# 23. DNS Troubleshooting

When Autodiscover is suspected, verify DNS.

Conceptually:

```text
User Domain
     ↓
DNS Lookup
     ↓
Autodiscover Record
     ↓
Expected Microsoft 365 Service
```

Check:

* DNS record exists
* Correct record type
* Correct target
* Public DNS visibility
* No conflicting records

---

# 24. Autodiscover DNS Failure

Example:

```text
Outlook
 ↓
Autodiscover lookup
 ↓
DNS failure
 ↓
Configuration failure
```

Possible symptoms:

* Account setup fails
* Autodiscover test fails
* Outlook cannot locate mailbox configuration

If DNS is managed by another team or provider, document the required correction and escalate appropriately.

---

# 25. Incorrect Autodiscover DNS Record

Example:

```text
autodiscover.company.com
        ↓
Incorrect destination
```

This can cause Outlook to connect to an incorrect service or fail to configure the mailbox.

Always validate the organization's intended Microsoft 365 configuration before changing DNS.

---

# 26. Multiple DNS Records

Conflicting or legacy DNS configuration can complicate troubleshooting.

Example:

```text
Autodiscover
   ↓
Multiple / Conflicting Configuration
   ↓
Unexpected Discovery Result
```

Review the actual DNS configuration and organization's mail architecture.

---

# 27. Hybrid Exchange Environments

Hybrid environments can involve:

```text
On-Premises Exchange
        +
Exchange Online
        +
Microsoft Entra ID
        +
Autodiscover
```

Therefore, Autodiscover troubleshooting in hybrid environments requires understanding which mailbox is hosted where.

---

# 28. Hybrid Mailbox Location

Before troubleshooting a hybrid environment, determine:

```text
User
 ↓
Mailbox Location
 ↓
On-Premises?
     OR
Exchange Online?
```

A mailbox location mistake can lead to incorrect troubleshooting assumptions.

---

# 29. Autodiscover and Profile Creation

When a new profile is created:

```text
New Profile
    ↓
Email Address
    ↓
Autodiscover
    ↓
Authentication
    ↓
Mailbox Configuration
    ↓
Profile Created
```

If profile creation fails, investigate Autodiscover before assuming the Outlook application itself is broken.

---

# 30. Autodiscover and Existing Profiles

If an existing Outlook profile worked previously but suddenly stopped:

```text
Previously Working
       ↓
New Failure
       ↓
Check:
- Account
- Authentication
- Service
- Autodiscover
- Profile
```

This is different from a brand-new profile failing during initial setup.

---

# 31. Outlook Autodiscover Test

Outlook provides diagnostic functionality for testing account configuration and connectivity.

A support engineer may use appropriate Outlook diagnostics to inspect Autodiscover behavior.

The exact interface varies by Outlook version.

When collecting diagnostic information, avoid exposing credentials or sensitive user data.

---

# 32. Microsoft Remote Connectivity Tests

Microsoft provides connectivity testing capabilities that can help administrators investigate Exchange-related connectivity and Autodiscover problems.

Use organization-approved Microsoft diagnostic tools and follow current Microsoft guidance.

---

# 33. PowerShell Troubleshooting

Exchange Online administrators can use PowerShell for administrative investigation.

Conceptually:

```text
PowerShell
    ↓
Exchange Online
    ↓
Mailbox Configuration
    ↓
Administrative Validation
```

Use only approved administrative commands and appropriate permissions.

Do not execute destructive commands during troubleshooting.

---

# 34. Autodiscover Troubleshooting Layers

A useful L2 troubleshooting model:

```text
Layer 1
User / Email Address
        ↓
Layer 2
Internet / Network
        ↓
Layer 3
DNS
        ↓
Layer 4
Autodiscover
        ↓
Layer 5
Authentication
        ↓
Layer 6
Exchange Online
        ↓
Layer 7
Outlook Profile
        ↓
Layer 8
Outlook Application
```

Work from the lowest confirmed failure point.

---

# 35. Scenario — New User Cannot Create Outlook Profile

### Incident

```text
New User
   ↓
Outlook Setup
   ↓
Email Entered
   ↓
Configuration Fails
```

Investigation:

```text
Check Account
      ↓
Check Microsoft 365 Login
      ↓
Check Outlook Web
      ↓
Check DNS
      ↓
Test Autodiscover
      ↓
Check Authentication
```

---

# 36. Scenario — Outlook Says Disconnected

### User Report

> "Outlook shows Disconnected."

Do not automatically classify this as an Autodiscover problem.

Investigate:

```text
Network
 ↓
Authentication
 ↓
Exchange Connectivity
 ↓
Outlook Profile
 ↓
Autodiscover
```

Autodiscover may be involved, but connectivity should be tested separately.

---

# 37. Scenario — Outlook Connects to Wrong Mailbox

Possible areas:

```text
User Account
 ↓
Outlook Profile
 ↓
Autodiscover
 ↓
Mailbox Configuration
```

Verify:

* Correct email address
* Correct Microsoft 365 account
* Correct profile
* Correct mailbox
* Correct authentication identity

---

# 38. Scenario — Autodiscover Works on One Computer

Example:

```text
Computer A
 ↓
Outlook works

Computer B
 ↓
Outlook setup fails
```

This suggests comparing:

* DNS
* Network
* Proxy
* Outlook version
* Office installation
* Cached credentials
* Local configuration

The Microsoft 365 service may already be functioning correctly.

---

# 39. Scenario — Autodiscover Fails Everywhere

Example:

```text
Computer A → Fail
Computer B → Fail
Outlook Web → Works
```

Investigate shared configuration such as:

```text
DNS
 ↓
Autodiscover
 ↓
Authentication
 ↓
Microsoft 365
```

This is more likely to be an environment/configuration issue than a single-device issue.

---

# 40. Scenario — Password Changed Recently

### User Report

> "I changed my Microsoft 365 password and Outlook is asking for credentials."

Investigation:

```text
Password Changed
      ↓
Authentication State
      ↓
Cached Credentials / Tokens
      ↓
Outlook
      ↓
Exchange Online
```

Use approved credential-remediation procedures.

Do not repeatedly delete credentials without first understanding the authentication flow.

---

# 41. L1 Support Checklist

```text
[ ] Confirm user email address
[ ] Confirm Internet connectivity
[ ] Test Microsoft 365 sign-in
[ ] Test Outlook Web
[ ] Confirm Outlook version
[ ] Check account status
[ ] Check authentication/MFA
[ ] Restart Outlook
[ ] Capture exact error
[ ] Document symptoms
```

---

# 42. L2 Support Checklist

```text
[ ] Verify mailbox location
[ ] Validate DNS
[ ] Test Autodiscover
[ ] Check authentication
[ ] Check Conditional Access where appropriate
[ ] Compare Web vs Desktop
[ ] Review Outlook profile
[ ] Check network/proxy configuration
[ ] Check hybrid configuration if applicable
[ ] Use approved diagnostic tools
[ ] Validate remediation
[ ] Document root cause
```

---

# 43. Autodiscover Troubleshooting Decision Tree

```text
                    Outlook Issue
                         ↓
                Can User Sign In?
                  /           \
                Yes            No
                 ↓              ↓
           Test Outlook Web   Identity /
                 ↓            Authentication
             Works?
             /    \
           Yes     No
            ↓       ↓
      Investigate  Check
       Desktop     Account /
       Outlook     Service
            ↓
       Autodiscover
            ↓
        DNS / Auth
            ↓
      Exchange Online
            ↓
        Test Again
```

---

# 44. Support Ticket Example

```text
Issue:
User unable to configure Microsoft 365 mailbox in Outlook.

Symptoms:
Outlook failed during automatic account setup.

Investigation:
Confirmed correct email address.
Verified Internet connectivity.
Confirmed user could sign in through Outlook Web.
Investigated Autodiscover configuration.
Validated DNS and authentication.
Tested Outlook configuration again.

Finding:
The issue was isolated to the Outlook client configuration rather than the Microsoft 365 mailbox.

Action:
Reconfigured the Outlook profile according to the approved support procedure.

Validation:
Outlook successfully completed mailbox configuration and connected to Exchange Online.

Status:
Resolved.
```

---

# 45. Best Practices

### Do

* Understand the Autodiscover flow
* Verify DNS before making changes
* Test Outlook Web
* Check authentication separately
* Identify mailbox location
* Compare affected and working devices
* Capture exact errors
* Follow Microsoft-supported diagnostic procedures
* Protect diagnostic information
* Document the root cause

### Don't

* Assume every Outlook problem is Autodiscover
* Immediately recreate profiles
* Change DNS without authorization
* Disable Conditional Access to solve a user issue
* Ask users to repeatedly enter passwords without investigation
* Expose credentials in troubleshooting documentation
* Make destructive Exchange changes during diagnosis

---

# 46. Key Takeaways

* Autodiscover helps Outlook discover mailbox configuration.
* DNS can be an important component of Autodiscover.
* Authentication and Autodiscover are related but separate troubleshooting areas.
* Outlook Web is valuable for isolating client-side problems.
* Outlook profile problems can look like Autodiscover problems.
* Hybrid Exchange environments require understanding mailbox location.
* Conditional Access and MFA can affect Outlook authentication.
* L2 troubleshooting should follow a layered approach.
* Always identify the actual failure point before applying a fix.

---

## Related Documentation

* [Outlook Overview](./01-Outlook-Overview.md)
* [Outlook Configuration](./02-Outlook-Configuration.md)
* [Outlook Account Setup](./03-Outlook-Account-Setup.md)
* [Outlook Profile](./04-Outlook-Profile.md)
* [Outlook Profile Creation](./05-Outlook-Profile-Creation.md)
* [Outlook Profile Corruption](./06-Outlook-Profile-Corruption.md)
* [Shared Mailbox](./17-Shared-Mailbox.md)
* [Distribution Groups](./18-Distribution-Groups.md)
* [Credential Prompts](./20-Credential-Prompts.md)
* [Outlook Connectivity](./21-Outlook-Connectivity.md)
* [Mail Send/Receive Issues](./23-Mail-Send-Receive-Issues.md)
* [Real-World Scenarios](./25-Real-World-Scenarios.md)
