# Microsoft 365 Domains

## 1. Overview

A domain is a key component of a Microsoft 365 environment.

Organizations commonly use their own business domain for:

- User sign-in
- Email addresses
- Microsoft 365 services
- Exchange Online
- Teams
- SharePoint
- OneDrive
- Application identities

Example:

```text
Company:
Contoso Ltd.

Custom Domain:
contoso.com

User:
john@contoso.com
````

Microsoft 365 also provides an initial `onmicrosoft.com` domain when a tenant is created.

---

# 2. Types of Domains

There are two important domain concepts to understand.

## Initial Domain

The initial domain is associated with the tenant when it is created.

Example:

```text
contoso.onmicrosoft.com
```

## Custom Domain

The organization can add its own domain.

Example:

```text
contoso.com
```

Simplified:

```text
Microsoft 365 Tenant
        │
        ├── Initial Domain
        │      └── contoso.onmicrosoft.com
        │
        └── Custom Domain
               └── contoso.com
```

---

# 3. Why Organizations Use Custom Domains

Organizations normally want employees to use their company identity.

Instead of:

```text
employee@contoso.onmicrosoft.com
```

they may use:

```text
employee@contoso.com
```

This provides a professional organizational identity.

Custom domains are especially important for:

* Email
* User sign-in
* Microsoft 365 identity
* Exchange Online
* Hybrid environments
* Business applications

---

# 4. Domain Verification

Before Microsoft 365 can use a custom domain, the organization generally needs to prove that it owns the domain.

A simplified process:

```text
Add Domain
    ↓
Microsoft Provides Verification Information
    ↓
Add DNS Record at DNS Provider
    ↓
Microsoft Checks DNS
    ↓
Domain Verified
    ↓
Configure Microsoft 365 Services
```

A TXT record is commonly used for domain verification.

---

# 5. DNS

DNS stands for:

**Domain Name System**

DNS translates domain names into information that computers and services can use.

For example:

```text
mail.contoso.com
        ↓
DNS
        ↓
Destination / DNS Information
```

Microsoft 365 administrators and support engineers should understand DNS because many Microsoft 365 services depend on correct DNS configuration.

---

# 6. Important DNS Record Types

The most important records for Microsoft 365 support are:

* A
* AAAA
* CNAME
* MX
* TXT
* SRV

Each record serves a different purpose.

---

# 7. A Record

An A record maps a hostname to an IPv4 address.

Example:

```text
server.contoso.com
        ↓
192.0.2.10
```

Conceptually:

```text
Hostname
   ↓
A Record
   ↓
IPv4 Address
```

A records are not normally the primary record used to configure Microsoft 365 email.

---

# 8. AAAA Record

An AAAA record maps a hostname to an IPv6 address.

Conceptually:

```text
Hostname
   ↓
AAAA Record
   ↓
IPv6 Address
```

---

# 9. CNAME Record

CNAME stands for:

**Canonical Name**

It creates an alias from one hostname to another hostname.

Simplified:

```text
alias.contoso.com
       ↓
CNAME
       ↓
target.example.com
```

Microsoft 365 uses CNAME records for certain service configurations.

---

# 10. MX Record

MX stands for:

**Mail Exchange**

An MX record tells sending mail systems where email for a domain should be delivered.

Simplified:

```text
Email:
user@contoso.com

        ↓

DNS Lookup

        ↓

MX Record

        ↓

Exchange Online
```

For Microsoft 365 email, the MX record normally points to the Microsoft-provided Exchange Online protection destination for the organization's domain.

---

# 11. Why MX Is Important

Suppose a user says:

> "External users cannot send email to me."

One thing an administrator may investigate is the domain's MX configuration.

Simplified troubleshooting:

```text
External Sender
      ↓
DNS Lookup
      ↓
MX Record
      ↓
Mail Destination
      ↓
Exchange Online
      ↓
Recipient Mailbox
```

If the MX configuration is incorrect, mail delivery can fail or be directed somewhere unexpected.

---

# 12. TXT Records

TXT records contain text-based DNS information.

Microsoft 365 commonly uses TXT records for purposes such as:

* Domain verification
* SPF
* Other service-specific configurations

Example concept:

```text
contoso.com
    ↓
TXT
    ↓
Verification / Policy Information
```

---

# 13. SPF

SPF stands for:

**Sender Policy Framework**

SPF helps receiving mail systems determine which servers are authorized to send email for a domain.

Simplified:

```text
Email Sender
     ↓
Sending Server
     ↓
Receiving Server
     ↓
Check SPF
     ↓
Is sender authorized?
```

For Microsoft 365, SPF is commonly published as a TXT record.

---

# 14. SPF Example

Conceptually:

```text
contoso.com
   ↓
TXT Record
   ↓
SPF Policy
   ↓
Authorized Sending Sources
```

A Microsoft 365 environment commonly uses a Microsoft-provided SPF mechanism as part of the domain's SPF record.

Important:

> An organization should have one effective SPF record for a domain.

If multiple separate SPF TXT records are published for the same domain, SPF evaluation can fail.

---

# 15. DKIM

DKIM stands for:

**DomainKeys Identified Mail**

DKIM uses cryptographic signing to help receiving mail systems verify that an email was authorized by the sending domain and that the signed message has not been improperly modified.

Simplified:

```text
Sender
  ↓
Email
  ↓
DKIM Signature
  ↓
Receiving Server
  ↓
Verify Signature
```

DKIM helps protect the authenticity of outgoing email.

---

# 16. DMARC

DMARC stands for:

**Domain-based Message Authentication, Reporting and Conformance**

DMARC builds on email authentication mechanisms such as SPF and DKIM.

Simplified:

```text
Email
  │
  ├── SPF
  │
  └── DKIM
       │
       ▼
     DMARC
       │
       ▼
Policy / Handling Decision
```

DMARC allows a domain owner to publish a policy describing how receiving systems should handle messages that fail authentication/alignment requirements.

---

# 17. SPF vs DKIM vs DMARC

| Technology | Main Purpose                                             |
| ---------- | -------------------------------------------------------- |
| SPF        | Identifies authorized sending sources                    |
| DKIM       | Cryptographically signs outgoing email                   |
| DMARC      | Defines policy and reporting around email authentication |

A simple way to remember:

```text
SPF
"Is this server authorized?"

DKIM
"Does this email have a valid signature?"

DMARC
"What should happen if authentication/alignment fails?"
```

---

# 18. Autodiscover

Autodiscover helps Outlook clients discover Exchange-related configuration.

Simplified:

```text
User
  ↓
Outlook
  ↓
Autodiscover
  ↓
Exchange Online
  ↓
Mailbox Configuration
```

Autodiscover can be important when troubleshooting:

* Outlook profile creation
* Account configuration
* Authentication
* Mailbox connectivity

---

# 19. Autodiscover and DNS

DNS can be involved in the process of discovering the appropriate Microsoft 365 service endpoints.

A simplified conceptual model is:

```text
Outlook
   ↓
Autodiscover
   ↓
DNS / Service Discovery
   ↓
Microsoft 365
   ↓
Exchange Online
```

Modern Microsoft 365 environments use Microsoft's service discovery and authentication architecture, so troubleshooting should not assume that a single traditional DNS record explains every Outlook connection.

---

# 20. SRV Records

SRV stands for:

**Service Record**

SRV records can identify the location of services for a domain.

Conceptually:

```text
Service
   ↓
SRV Record
   ↓
Target Host + Port
```

Microsoft 365 may use SRV records for certain service discovery scenarios.

---

# 21. Microsoft 365 Domain Configuration

A typical domain setup may look like:

```text
                    contoso.com
                         │
             ┌───────────┼───────────┐
             │           │           │
             ▼           ▼           ▼
            MX          TXT        CNAME
             │           │           │
             ▼           ▼           ▼
          Email      Verification   Service
             │       / SPF          Config
             ▼
      Exchange Online
```

Additional DNS records may be required depending on the Microsoft 365 services and configuration being used.

---

# 22. Email Flow and DNS

A simplified inbound email flow:

```text
External Sender
      ↓
Recipient Domain
      ↓
DNS Lookup
      ↓
MX Record
      ↓
Exchange Online
      ↓
Security Filtering
      ↓
Mailbox
      ↓
Outlook
```

A simplified outbound flow:

```text
User
 ↓
Outlook
 ↓
Exchange Online
 ↓
Mail Flow / Security
 ↓
External Recipient
 ↓
Receiving Mail System
```

---

# 23. DNS and Email Troubleshooting

### Scenario

> "Nobody outside the company can send email to our users."

Possible investigation:

```text
External Sender
      ↓
Check Recipient Domain
      ↓
DNS Lookup
      ↓
Check MX
      ↓
Check Mail Destination
      ↓
Check Exchange Online
      ↓
Check Mail Flow
      ↓
Check Message Trace
      ↓
Check Quarantine / Security
```

Potential causes include:

* Incorrect MX record
* DNS propagation/change issue
* Mail flow configuration
* Exchange Online issue
* Recipient mailbox issue
* Security filtering
* Domain configuration problem

---

# 24. DNS Troubleshooting Commands

An IT support engineer can use DNS tools to investigate domain configuration.

### Windows

```powershell
nslookup contoso.com
```

Check MX:

```powershell
nslookup -type=MX contoso.com
```

Check TXT:

```powershell
nslookup -type=TXT contoso.com
```

Check CNAME:

```powershell
nslookup -type=CNAME autodiscover.contoso.com
```

### PowerShell

Depending on the environment, PowerShell DNS commands can also be used.

Example:

```powershell
Resolve-DnsName contoso.com
```

MX:

```powershell
Resolve-DnsName contoso.com -Type MX
```

TXT:

```powershell
Resolve-DnsName contoso.com -Type TXT
```

---

# 25. Scenario — Domain Verification Failure

### User/Administrator reports:

> "We added our domain but Microsoft 365 cannot verify it."

Investigation:

```text
Custom Domain
      ↓
Check DNS Provider
      ↓
Check Verification Record
      ↓
Check Record Name
      ↓
Check Record Value
      ↓
Check DNS Propagation
      ↓
Retry Verification
```

Common causes:

* Incorrect TXT value
* Incorrect DNS record name
* Record added to the wrong DNS zone
* DNS propagation delay
* Existing DNS configuration conflicts

---

# 26. Scenario — Email Not Arriving

### Problem

```text
User:
"I am not receiving external emails."
```

Investigation:

```text
1. Confirm sender
       ↓
2. Confirm recipient address
       ↓
3. Check MX
       ↓
4. Check Exchange Online
       ↓
5. Check Message Trace
       ↓
6. Check Quarantine
       ↓
7. Check Mail Flow Rules
       ↓
8. Check Anti-Spam / Security
       ↓
9. Check Mailbox
       ↓
10. Validate
```

---

# 27. Scenario — Email Going to Spam

### Problem

> "Emails from our application are going to spam."

Possible investigation:

```text
Sending System
      ↓
SPF
      ↓
DKIM
      ↓
DMARC
      ↓
Sender Reputation
      ↓
Microsoft Defender
      ↓
Exchange Online Filtering
      ↓
Recipient Mailbox
```

Do not assume that SPF alone guarantees inbox delivery.

---

# 28. Scenario — SPF Failure

Possible investigation:

```text
Email Sent
    ↓
Receiving System
    ↓
SPF Check
    ↓
Authorized Sender?
   ┌───────┴───────┐
  YES             NO
   │               │
   ▼               ▼
Continue       SPF Failure
```

If an organization sends mail through multiple legitimate platforms, the SPF configuration must account for all authorized sending sources while staying within SPF's evaluation limits.

---

# 29. Scenario — DKIM Failure

Possible investigation:

```text
Email
  ↓
DKIM Signature
  ↓
Receiving System
  ↓
DNS Public Key Lookup
  ↓
Signature Validation
  ↓
Pass / Fail
```

Potential causes can include:

* Incorrect DKIM configuration
* DNS record problems
* Invalid signing configuration
* Domain configuration issues

---

# 30. Scenario — DMARC Failure

A simplified investigation:

```text
Email
  ↓
SPF Result
  ↓
DKIM Result
  ↓
Alignment
  ↓
DMARC Evaluation
  ↓
Policy
  ↓
Receiving System Decision
```

DMARC troubleshooting requires understanding both authentication and domain alignment.

---

# 31. Domain Troubleshooting Checklist

When troubleshooting a Microsoft 365 domain:

### Domain

* Is the domain registered?
* Is the domain verified?
* Is the correct DNS zone being modified?

### DNS

* Are records present?
* Are records correct?
* Has DNS propagated?

### Email

* Is MX correct?
* Is SPF configured?
* Is DKIM configured?
* Is DMARC configured?

### Exchange Online

* Is the mailbox available?
* Is mail flow working?
* Are transport rules affecting the message?
* Is the message in quarantine?

### Client

* Is Outlook configured correctly?
* Is Autodiscover working?
* Is authentication successful?

---

# 32. Common DNS Mistakes

Common mistakes include:

### Mistake 1 — Wrong DNS Provider

The administrator changes DNS records at a provider that is not authoritative for the domain.

### Mistake 2 — Incorrect Record Value

A Microsoft-provided value is entered incorrectly.

### Mistake 3 — Duplicate SPF Records

Multiple SPF TXT records are created instead of maintaining one effective SPF policy.

### Mistake 4 — Incorrect MX

Mail is routed to the wrong destination.

### Mistake 5 — Missing DKIM Configuration

The organization expects DKIM authentication but has not correctly configured the required DNS records and service settings.

### Mistake 6 — Incorrect DMARC Policy

A DMARC policy is deployed without understanding its impact on legitimate email sources.

---

# 33. L1 Support Perspective

L1 support may handle:

* Basic DNS verification checks
* Basic domain troubleshooting
* Checking MX/TXT records
* Collecting error messages
* Running `nslookup`
* Checking Outlook configuration
* Escalating DNS or mail-flow problems

---

# 34. L2 Support Perspective

L2 support may investigate:

* DNS configuration
* Exchange Online mail flow
* Message Trace
* SPF
* DKIM
* DMARC
* Autodiscover
* Mail flow rules
* Connectors
* Quarantine
* Authentication
* Domain configuration
* Root cause

---

# 35. Interview Questions

## Q1. What is DNS?

DNS is the Domain Name System. It translates domain names into information used by computers and services to locate and communicate with resources.

## Q2. What is an MX record?

An MX record identifies the mail servers responsible for receiving email for a domain.

## Q3. What is SPF?

SPF is an email authentication mechanism that identifies authorized sending sources for a domain.

## Q4. What is DKIM?

DKIM uses cryptographic signatures to help receiving systems verify that an email was authorized by the sending domain and that the signed content has not been improperly modified.

## Q5. What is DMARC?

DMARC is an email authentication policy and reporting framework that builds on SPF and DKIM and uses domain alignment to help receiving systems determine how to handle messages that fail authentication requirements.

## Q6. What is the difference between SPF, DKIM, and DMARC?

```text
SPF
→ Authorized sending sources

DKIM
→ Cryptographic email signature

DMARC
→ Policy + reporting + authentication alignment
```

## Q7. A company cannot receive external email. What would you check?

I would check the recipient domain's MX records first, then investigate Exchange Online mail flow, Message Trace, connectors, transport rules, security filtering, quarantine, and mailbox configuration.

## Q8. What command can you use to check an MX record?

```powershell
nslookup -type=MX contoso.com
```

or:

```powershell
Resolve-DnsName contoso.com -Type MX
```

## Q9. What is Autodiscover?

Autodiscover is a service-discovery mechanism used by Outlook and Exchange clients to obtain appropriate configuration information for connecting to Exchange services.

## Q10. Why is DNS knowledge important for Microsoft 365 support?

Because Microsoft 365 services, particularly domain verification, email delivery, authentication-related configurations, and service discovery, can depend on correct DNS configuration.

---

# 36. Portfolio Learning Outcome

After completing this topic, I should be able to:

* Explain Microsoft 365 domains.
* Explain initial and custom domains.
* Understand domain verification.
* Explain DNS fundamentals.
* Explain A, AAAA, CNAME, MX, TXT, and SRV records.
* Explain SPF.
* Explain DKIM.
* Explain DMARC.
* Understand the relationship between DNS and Exchange Online.
* Understand basic Autodiscover concepts.
* Troubleshoot common domain issues.
* Troubleshoot basic email routing problems.
* Use `nslookup` and `Resolve-DnsName`.
* Approach Microsoft 365 email authentication issues systematically.
* Explain domain and DNS concepts during technical interviews.

# 38. Next Topic

The next topic is:

Microsoft 365 Users and Groups

Topics will include:

* User accounts
* Guest users
* Member users
* User Principal Name
* Security groups
* Microsoft 365 groups
* Distribution groups
* Dynamic groups
* Group ownership
* Group membership
* Group-based licensing
* User lifecycle
* Joiner/Mover/Leaver process
* User troubleshooting
* Group troubleshooting
