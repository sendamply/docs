# Analytics Overview

Amply's powerful analytics engine automatically extracts insight from your email. This data is used for business and email health indicators, and to answer difficult questions like:

- How is your business acquiring and engaging users?
- Where are most of your users engaging from?
- When is the most common time for **{insert event}**
- What is the impact of my new feature on **{insert goal event}**

In addition to being accessible from the Amply dashboard, all of your data and visualizations can be queried from our API. We store all engagement data indefinitely, which helps you identify trends for your business.

### Getting Value from your Data

<!--
type: tab
title: Ops + Engineering Teams
-->

### Ops + Engineering Teams

- [Deliverability strategies](../Deliverability/150-Deliverability-Strategy.md) to add redundancy to your email infrastructure
- Real-time monitoring of spam data and DNSBLs (IP blocklists)
- Centralized logs of email activity and content that is queryable via SQL
- Easily troubleshoot problems with the full contents and headers of sent emails

<!--
type: tab
title: Security Teams
-->

### Security Teams

- Easily investigate phishing cases with an audit trail of all email activity and metadata (stored indefinitely)
- IP/country allowlist and blocklist that notifies you on violations
- (Coming soon) Anomaly detection to receive notifications on phished and compromised acccounts

<!--
type: tab
title: Marketing Teams
-->

### Marketing Teams

- Insight to see if your marketing campaigns are effective
- Detailed demographics and user information

<!--
type: tab
title: Sales + Support Teams
-->

### Sales + Support Teams

- Detailed user profiles with full activity feed that can be connected to your CRM
- Easily identify engaged and unengaged users to increase conversions and decrease churns

<!-- type: tab-end -->

### Types of Data

Amply collects two types of data: **email activity** and **email contents**. This data is easily queryable from our API or in your dashboard by clicking on the SQL page under the Analytics tab.

**email_activities**

| Field | Details |
| --------- | ---------- |
| **activity_type_id** | The type of activity. Can be sends, opens, clicks, bounces, spam_reports, unsubscribes, inbounds.|
**browser** | A string containing the browser.
**categories** | A comma seperated string containing tagged email categories.
**city** | A string containing the city. We ignore this field if it has been proxied.
**country** | A string containing the country. We ignore this field if it has been proxied.
**created_at** | An iso8601 formatted string containing the time of the event.
**email_client** | A string containing the email client.
**error** | A string containing the error (if any).
**from** | A string containing the header from.
**href** | A string containing the link (if a click event).
**ip_address** | A string containing the IP address of the recipient.
**latitude** | A string containing the latitude that has been derived from the ip_address. We ignore this field if it has been proxied.
**longitude** | A string containing the longitude that has been derived from the ip_address. We ignore this field if it has been proxied.
**message_id** | A string containing the message id from the email content.
**outbound_ip_address** | A string containing the IP address that sent the email.
**recipient** | A string containing the email address of the recipient.
**state** | A string containing the city. We ignore this field if it has been proxied.
**subject** | A string containing the subject from the email content.

**email_contents**

| Field | Details |
|---------|----------|
**attachments** | A JSON string containing a list of attachments and file types.
**headers** | A string seperated by carriage returns `\r\n` containing the headers.
**html** | A string containing the HTML contents.
**message_id** | A string containing the message id.
**text** | A string containing the text contents.
