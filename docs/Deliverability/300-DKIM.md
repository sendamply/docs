# DKIM

DKIM stands for DomainKeys Identified Mail and is an email authentication method to help prevent spoofing.

DKIM lets an email server associate its name with a sending domain by affixing an email signature of the email contents to the email headers. An email client can calculate the signature using the sending domain's DNS records (which is public to the internet) and compare this against the signature sent in the "DKIM-Signature" header in the email that was sent. If the two signatures are equal, then the email client can be sure that the email was sent by an authorized domain.

****

### DKIM Alignment

DKIM alignment is when your DKIM signing domain matches the Header From domain. The two types of DKIM alignment are relaxed alignment and strict alignment. If you do not specify strict alignment, relaxed alignment is assumed.

#### Relaxed Alignment

This alignment type requires the DKIM domain to match the root Header From domain. Relaxed alignment is the default. Relaxed alignment allows a subdomain to be used and still meet the domain alignment requirement.

<!-- theme: success -->
> **Valid Alignment**
>
> If your DKIM domain is **mail.example.com** and your Header From is **example.com**, your email would pass DKIM alignment. The root domains **example.com** match.

<!-- theme: danger -->
> **Invalid Alignment**
>
> If your DKIM domain is **example.mail.com** and your Header From is **example.com**, your email would not pass DKIM alignment. The root domains **mail.com** and **example.com** do not match.

#### Strict Alignment

This alignment type requires the DKIM domain to match the Header From domain exactly.

<!-- theme: success -->
> **Valid Alignment**
>
> If your DKIM domain is **mail.example.com** and your Header From domain is **mail.example.com**, your email would pass DKIM alignment.

<!-- theme: danger -->
> **Invalid Alignment**
>
> If your DKIM domain is **mail.example.com** and your Header From domain is **example.com**, your email would not pass DKIM alignment.

****

### Setting your DKIM Domain

By default, Amply will automatically sign your emails using our hosts. When you [verify your domain](./100-Sender-Verification.md#domain-verification), you'll need to set a DNS record at amp._domainkey.yourdomain.com.

The record you should add is a simple CNAME and will look something like this:


> NAME amp._domainkey.yourdomain.com IN CNAME "amp._domainkey.yourhost.smtp.sendamply.net"
