# What are Webhooks?

Webhooks notify a URL of your choice via HTTP POST with information that occurs as Amply processes your email and users' activity.

Your webhook can be configured from the Settings page. In addition to providing a URL, you also have the option to set an access key. This access key is different than the ones you provision to authenticate for relay or API access. This access key is a value that you control so that your application can securely authenticate its endpoints.


## Email Blacklist Monitoring

Receive an event when one of your IP addresses is added to a blacklist. The following params will be sent:



```json
["webhook_event"] => "email_blacklist",
["access_key"]    => "your_access_key_here",
["blacklists"]    => ["blacklist1", "blacklist2"], # json string
["ip_address"]    => "1.2.3.4"
```

Click here to send a test request to the webhook configured in your Settings page.


## Country Monitoring

Receive an event when one of your users accesses an email that you sent from an unauthorized country. The following params will be sent:

```json
["webhook_event"] => "country_monitoring",
["access_key"]    => "your_access_key_here",
["email_address"] => "test@sendamply.com",
["country"]       => "Nigeria",
["ip_address"]    => "1.2.3.4",
["email_id"]      => "1"
```

Click here to send a test request to the webhook configured in your Settings page.

## Inbound Parse

**Introduction**

Amply can help you process email using the Inbound Parse Webhook. This webhook processes all incoming email for a domain or subdomain, parses the contents and attachments, then POSTs multipart/form-data to a URL that you choose.

To begin processing email using Amply's Inbound Parse Webhook, you will have to setup MX Records, choose the receiving domain that will be receiving the emails you want to parse, and define the URL where you want to POST your parsed emails.

**Step 1: Set your MX Record**

1. Navigate to the MX Records page on your hosting provider’s website. If you’re unsure who your hosting or DNS provider is, please contact your website administrator.
2. Create a new MX record for the subdomain (e.g. inboundparsetest.yourdomain.com) you want to process incoming email. It is important that this domain is exclusively used to parse your incoming email.
3. Assign the MX record a priority of 10, and point it to the address: mx.sendamply.com.

It should look like this:



