# SPF

SPF stands for Sender Policy Framework and is an email validation protocol designed to detect and block email spoofing by providing a way for email clients to verify that incoming mail from a domain comes from an IP Address authorized by that domain's administrators.

SPF is one of the most important mechanisms for email deliverability and is required to authorize Amply to send email on your organization's behalf.

****

## SPF Alignment

SPF alignment is when your Envelope From domain matches the Header From domain. The two types of SPF alignment are relaxed alignment and strict alignment. If you do not specify strict alignment, relaxed alignment is assumed.

****

### Relaxed Alignment

With relaxed alignment, only the root domain of the Envelope From address must match the root domain of the Header From address. Relaxed alignment allows a subdomain to be used and still meet the domain alignment requirement.

**For example:**

If your Envelope From domain is mail.example.com and your Header From is example.com, your email would pass SPF alignment. The root domains example.com match.

If your Envelope From domain is example.mail.com and your Header From is example.com, your email would not pass SPF alignment. The root domains mail.com and example.com do not match.

****

### Strict Alignment

With strict alignment, the domain of the Envelope address is an exact match for the domain of the Header From address.

**For example:**

If your Envelope From domain is mail.example.com and your Header From is mail.example.com, your email would pass SPF alignment.

If your Envelope From domain is mail.example.com and your Header From is example.com, your email would not pass SPF alignment.

****

## Setting your SPF Domain

In order to determine if the email server is authorized to send mail from that address, an email client will look up the DNS record for yourdomain.com. This record is a simple TXT record and may look something like this:

> NAME yourdomain.com IN TXT "v=spf1 include:yourhost.smtp.sendamply.com ~all"

The above SPF record authorizes Amply to send email on behalf of yourdomain.com. As long as the server sending email matches this domain, the email will pass the SPF check. If not, the email client will be unable to verify the sender identity and will most likely flag your email as spam.
