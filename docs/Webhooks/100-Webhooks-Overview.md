# Webhooks Overview

Webhooks notify a URL of your choice via HTTP POST with information that occurs as Amply processes your email and users' activity. Your webhook can be configured from the General page under the Mail Settings tab.

****

### Email Blacklist Monitoring

Receive an event when one of your IP addresses is added to a DNSBL blacklist. The following params will be sent:



```json
["webhook_event"] => "email_blacklist",
["blacklists"]    => ["blacklist1", "blacklist2"], # json string
["ip_address"]    => "1.2.3.4"
```

****

### Country Monitoring

Receive an event when one of your users accesses an email that you sent from an unauthorized country. The following params will be sent:

```json
["webhook_event"] => "country_monitoring",
["user"]          => "user@domain.com",
["country"]       => "Nigeria",
["ip_address"]    => "1.2.3.4",
["subject"]       => "Hello!",
["message_id"]    => "messageid@yourdomain.com"
```

****

### IP Monitoring

Receive an event when one of your users accesses an email that you sent from an unauthorized IP address. The following params will be sent:

```json
["webhook_event"] => "ip_monitoring",
["user"]          => "user@domain.com",
["ip_address"]    => "1.2.3.4",
["subject"]       => "Hello!",
["message_id"]    => "messageid@yourdomain.com"
```