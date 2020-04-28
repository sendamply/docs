# Webhooks Overview

### What are Webhooks?

Webhooks notify a URL of your choice via HTTP POST with information that occurs as Amply processes your email and users' activity.

Your webhook can be configured from the Settings page. In addition to providing a URL, you also have the option to set an access key. This access key is different than the ones you provision to authenticate for relay or API access. This access key is a value that you control so that your application can securely authenticate its endpoints.


### Email Blacklist Monitoring

Receive an event when one of your IP addresses is added to a blacklist. The following params will be sent:



```json
["webhook_event"] => "email_blacklist",
["access_key"]    => "your_access_key_here",
["blacklists"]    => ["blacklist1", "blacklist2"], # json string
["ip_address"]    => "1.2.3.4"
```

Click here to send a test request to the webhook configured in your Settings page.


### Country Monitoring

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
 
