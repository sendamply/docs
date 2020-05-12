# Quickstart Guide

Learn how to start sending email with Amply in just a few minutes. 

In this guide we'll go over how to verify your domain, set up your DNS records with the proper authentication protocols and send email either via our SMTP relay or REST API.


## How to Verify your Domain

The first thing you need to do once you've created your account and added your domain is to verify it. 

To do so:

1. Open your DNS provider and add the three TXT DNS records - SPF, DKIM, DMARC.

2. If you want Amply to track clicks and opens add the CNAME record.

Once the changes you've made to your DNS records take effect your domain will be verified.


### Verifying your domain is important for a few reasons:

- confirms you are authorized to send for your domain.

- helps you build a positive domain reputation.

- protects your email from spoofing attempts


## Set up DNS TXT Records 

- SPF: email validation protocol. More info on SPF here.
- DKIM: email validation protocol that uses a digital signature to confirm authenticity of messages. More info on DKIM here.
- DMARC: email validation method that informs senders on what messages are authenticating or not. More info on DMARC here.
- CNAME: Tracks opens and clicks (unsubscribe links).


Type | Value | Purpose
---------|----------|---------
 TXT | “value=spf1 include:amply.com ~all” | SPF (Required)
 TXT | "value=DKIM1" | DKIM (Required)
 TXT | "value=DMARC1" | DMARC (Required)
 CNAME | “amply.com” | Tracking (Required)



"You can check to see if the DNS value has updated using a service like [Whats My DNS](https://www.whatsmydns.net/).



### Update your Domain Records with your DNS Provider

You will need access to your domain registrar in order to complete the verification process for your sending domain. 

We have listed a few of the most popular DNS providers below with additional info. Please contact your DNS administrator directly if yours is not listed here.

[Cloudflare](https://www.cloudflare.com/plans/?utm_expid=.7pphc_ZaTHiTiyD0kMWvaA.0&utm_referrer=https%3A%2F%2Fwww.sparkpost.com%2Fdocs%2Fgetting-started%2Fgetting-started-sparkpost%2F)

[GoDaddy](https://www.godaddy.com/help/manage-dns-zone-files-680)

[NameCheap](https://www.namecheap.com/)

[RackSpace](https://support.rackspace.com/)


## Send with STMP Relay or REST API

Once your domain is verified, you can start sending email.

There are two ways to send email with Amply: through our **SMTP relay** or **REST API**. Both are highly effective methods of delivering email so choose whatever is best for your use case. Here are a few things to keep in mind:


SMTP Relay | REST API
---------|----------
 Easy to set up and integrate | Faster delivery (less back and forth between servers)
 Platform independent | Expanded functionality but more complex (technical)
 Established email standard | More robust


> SMTP is a widely adopted email protocol, while REST API offers you more flexibility in how you wish to operate.


### Send with SMTP

Sending email through our SMTP relay is the easiest way for an application to use Amply because it only requires updating your SMTP configuration in 4 simple steps.

1. Change your SMTP username to the username of the Pool or IP Address you want to send from. For most use cases, you should use the Global Pool.
2. Set the SMTP password of the relay to one of your live access tokens.
3. Set the SMTP host of the relay to smtp.sendamply.com.
4. Use port 465 for TLS connections and port 587 or 2525 for plain connections. 587 and 2525 can be made secure by upgrading the connection with the STARTTLS command, which is supported by most mail clients.


### Send with REST API

Run this code:

The Amply REST API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. JSON is returned by all API responses, including errors.

The REST API has some advantages over SMTP:

- If your ISP or hosting provider blocks traffic on mail ports.
- If you do not control your hosting environment and cannot install/configure an SMTP library.

For more details check out our full API reference here.


That's it! You're ready to get started!


