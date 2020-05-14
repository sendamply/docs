# DMARC

DMARC stands for Domain-based Message Authentication, Reporting and Conformance and is an email-validation system designed to detect and prevent email spoofing by solving operational and reporting issues related to the SPF and DKIM email authentication protocols.

DMARC instructs mailbox providers on how to handle unauthenticated email through a DMARC policy that you create in a DNS TXT record. This removes any guesswork on how mailbox providers should handle messages that fail DMARC authentication.

****

## Setting your DMARC Record

To pass DMARC, your email must pass either or both of:

- SPF authentication and SPF alignment (Header From and Envelope From domains match)
- DKIM authentication and DKIM alignment (Signing domain and Header From domain match)

Mailbox providers send regular DMARC aggregate and forensic reports back to senders, giving you visibility into what messages are authenticating, what messages are not and why.

The following table illustrates some of the configuration options you can specify when creating your DMARC record:


Tag | Purpose | Example
---------|----------|---------
 v | Protocol version | v=DMARC1
 pct | Percentage of messages subjected to filtering | pct=15
 ruf | Reporting URI for forensic reports | ruf=mailto:authfail@example.com
 rua | Reporting URI of aggregate reports | rua=mailto:aggrep@example.com
 p | Policy for organizational domain | p=quarantine
 sp | Policy for the subdomains of the organizational domain | sp=reject
 adkim | Alignment mode for DKIM | adkim=r
 aspf | Alignment mode for SPF | aspf=s


For example, the following DMARC record will notify postmaster@example.com and send the email to spam (p=quarantine) on a failed check:

> NAME _dmarc.example.com IN TXT  "v=DMARC1; p=quarantine; rua=mailto:postmaster@example.com"

**Important:** If your records are not aligned, make sure that you set your policy to none, instead of quarantine or reject. Although quarantine and reject will increase your deliverability rate, DMARC will fail if your records are not aligned and your email will automatically be sent to spam or be rejected.
