# DMARC

DMARC stands for Domain-based Message Authentication, Reporting and Conformance and is an email-validation system designed to detect and prevent email spoofing by solving operational and reporting issues related to the SPF and DKIM email authentication protocols.

DMARC instructs mailbox providers on how to handle unauthenticated email through a DMARC policy that you create in a DNS TXT record. This removes any guesswork on how mailbox providers should handle messages that fail DMARC authentication.

Setting an enforced DMARC policy (either *quarantine* or *reject* in the *p* tag) will greatly improve deliverability, and is a necessary step for low volume senders (less than 500 emails per day) who have not established a sending reputation.

****

### Setting your DMARC Record

To pass DMARC, your email must pass either or both of:

- SPF authentication and SPF alignment (Header From and Return-Path domains match)
- DKIM authentication and DKIM alignment (DKIM Signing domain and Header From domain match)

Mailbox providers send regular DMARC aggregate and forensic reports back to senders, giving you visibility into what messages are authenticating, what messages are not and why.

The following table illustrates some of the configuration options you can specify when creating your DMARC record:


Tag | Purpose | Values | Example
---------|----------|---------
 v | Protocol version | DMARC1 | v=DMARC1
 pct | Percentage of messages subjected to filtering | Number from 0 to 100 | pct=15
 ruf | Reporting URI for forensic reports | mailto address |ruf=mailto:authfail@example.com
 rua | Reporting URI of aggregate reports | mailto address | rua=mailto:aggrep@example.com
 p | Policy for organizational domain | none - no action is taken<br/>quarantine - failing messages are sent to spam folder<br/>reject - failing messsages are not delivered | p=quarantine
 sp | Policy for the subdomains of the organizational domain |none - no action is taken<br/>quarantine - failing messages are sent to spam folder<br/>reject - failing messsages are not delivered  | sp=reject
 adkim | Alignment mode for DKIM | r (relaxed) or s (strict) |adkim=r
 aspf | Alignment mode for SPF | r (relaxed) or s (strict) | aspf=s


For example, the following DMARC record will notify postmaster@example.com and send the email to spam (p=quarantine) on a failed check:

> NAME _dmarc.example.com IN TXT  "v=DMARC1; p=quarantine; rua=mailto:postmaster@example.com"

**Important:** If your records are not aligned, make sure that you set your policy to none, instead of quarantine or reject. Although quarantine and reject will increase your deliverability rate, DMARC will fail if your records are not aligned and your email will automatically be sent to spam or be rejected.