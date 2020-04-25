# Integrate

## SMTP Relay

Sending email through our SMTP relay is the easiest way for an application to use Amply because it only requires updating your SMTP configuration.

1. Change your SMTP username to the username of the Pool or IP Address you want to send from. For most use cases, you should use the Global Pool.
2. Set the SMTP password of the relay to one of your live access tokens.
3. Set the SMTP host of the relay to smtp.sendamply.com.
4. Use port 465 for TLS connections and port 587 or 2525 for plain connections. 587 and 2525 can be made secure by upgrading the connection with the STARTTLS command, which is supported by most mail clients.


**Frameworks**

Django

Laravel

Node.js

Ruby on Rails


## REST API

The REST API has some advantages over SMTP:

- If your ISP or hosting provider blocks traffic on mail ports.
- If you do not control your hosting environment and cannot install/configure an SMTP library.

You can look at the full API documentation here.


### Domain Integration

There are a couple steps to complete in order for Amply to send email on behalf of your domain and maximize the deliverability rate for your email.


**Marketing Email**

To send marketing email on behalf of your domain, you'll need to verify that you have control of the mailbox you send from. The best way to do this (which will give you the highest delivery rate) is to follow the steps below from the "Transactional Email" section. If you cannot update your DNS records, then you can still verify an individual mailbox by navigating to the campaign page and clicking on "Verify New Email Address". If you complete the steps in the "Transactional Email" section, then you can skip verifying your mailbox.


**Transactional Email**

In order to achieve the highest level of deliverability for your email, you'll want to add DNS records that implement SPF, DKIM, and DMARC. Updating these DNS entries should only take a few minutes and can be done by logging into your DNS provider (like GoDaddy, Rackspace, or Route53). If you have any questions, we are happy to walk you through the process. You can contact us here and we'll have one of our engineers help you out.

Once you've updated these records, we recommend that you set up your rDNS (reverse DNS) records. This is especially important for high volume senders and greatly increases your deliverability. The first step is to verify your domain from the verified domain page.

After verifying your domain, you're ready to update rDNS. Navigate to your IP page and click on the IP address you want to update. From the "rDNS" section, select the verified domain you want to send mail from, and then create a unique subdomain. We recommend something like "ip1.yourdomain.com", but it doesn't really matter what subdomain you choose; it just has to be unique and the host part (yourdomain.com) matches your verified domain. Make sure you create a valid A record in your DNS settings that points to the IP address you are configuring:

> NAME ip1.yourdomain.com IN A "1.2.3.4"

Congratulations, you're done setting up your email infrastructure!


### DKIM

DKIM stands for DomainKeys Identified Mail and is an email authentication method to help prevent spoofing. DKIM lets an email server associate its name with a sending domain by affixing an email signature of the email contents to the email headers. An email client can calculate the signature using the sending domain's DNS records (which is public to the internet) and compare this against the signature sent in the "DKIM-Signature" header in the email that was sent. If the two signatures are equal, then the email client can be sure that the email was sent by an authorized domain.


**DKIM Alignment**

DKIM alignment is when your DKIM signing domain matches the Header From domain. The two types of DKIM alignment are relaxed alignment and strict alignment. If you do not specify strict alignment, relaxed alignment is assumed.


**Relaxed Alignment**

This alignment type requires the DKIM domain to match the root Header From domain. Relaxed alignment is the default. Relaxed alignment allows a subdomain to be used and still meet the domain alignment requirement.

For example:

If your DKIM domain is mail.example.com and your Header From is example.com, your email would pass DKIM alignment. The root domains example.com match.

If your DKIM domain is example.mail.com and your Header From is example.com, your email would not pass DKIM alignment. The root domains mail.com and example.com do not match.


**Strict Alignment**

This alignment type requires the DKIM domain to match the Header From domain exactly.

For example:

If your DKIM domain is mail.example.com and your Header From domain is example.com, your email would not pass DKIM alignment.

If your DKIM domain is mail.example.com and your Header From domain is mail.example.com, your email would pass DKIM alignment.


**Setting your DKIM Domain**

By default, Amply will automatically sign your emails using our hosts. In order to set up rDNS and properly align your signing domain, you'll need to set a DNS record at amp._domainkey.yourdomain.com. If you don't care about setting up rDNS, you can skip this section.

The record you should add is a simple CNAME and will look something like this:


> NAME amp._domainkey.yourdomain.com IN CNAME "amp._domainkey.yourhost.smtp.sendamply.com"


Your organization's DKIM record is located at amp._domainkey.yourhost.smtp.sendamply.com.


### SPF

SPF stands for Sender Policy Framework and is an email validation protocol designed to detect and block email spoofing by providing a way for email clients to verify that incoming mail from a domain comes from an IP Address authorized by that domain's administrators.

SPF is one of the most important mechanisms for email deliverability and is required to authorize Amply to send email on your organization's behalf.


**SPF Alignment**

SPF alignment is when your Envelope From domain matches the Header From domain. The two types of SPF alignment are relaxed alignment and strict alignment. If you do not specify strict alignment, relaxed alignment is assumed.


**Relaxed Alignment**

With relaxed alignment, only the root domain of the Envelope From address must match the root domain of the Header From address. Relaxed alignment allows a subdomain to be used and still meet the domain alignment requirement.

For example:

If your Envelope From domain is mail.example.com and your Header From is example.com, your email would pass SPF alignment. The root domains example.com match.

If your Envelope From domain is example.mail.com and your Header From is example.com, your email would not pass SPF alignment. The root domains mail.com and example.com do not match.


**Strict Alignment**

With strict alignment, the domain of the Envelope address is an exact match for the domain of the Header From address.

For example:

If your Envelope From domain is mail.example.com and your Header From is mail.example.com, your email would pass SPF alignment.

If your Envelope From domain is mail.example.com and your Header From is example.com, your email would not pass SPF alignment.


**Setting your SPF Domain**

In order to determine if the email server is authorized to send mail from that address, an email client will look up the DNS record for yourdomain.com. This record is a simple TXT record and may look something like this:

> NAME yourdomain.com IN TXT "v=spf1 include:yourhost.smtp.sendamply.com ~all"

The above SPF record authorizes Amply to send email on behalf of yourdomain.com. As long as the server sending email matches this domain, the email will pass the SPF check. If not, the email client will be unable to verify the sender identity and will most likely flag your email as spam.


### DMARC

DMARC stands for Domain-based Message Authentication, Reporting and Conformance and is an email-validation system designed to detect and prevent email spoofing by solving operational and reporting issues related to the SPF and DKIM email authentication protocols.

DMARC instructs mailbox providers on how to handle unauthenticated email through a DMARC policy that you create in a DNS TXT record. This removes any guesswork on how mailbox providers should handle messages that fail DMARC authentication.

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

Important: if your records are not aligned, make sure that you set your policy to none, instead of quarantine or reject. Although quarantine and reject will increase your deliverability rate, DMARC will fail if your records are not aligned and your email will automatically be sent to spam or be rejected.







