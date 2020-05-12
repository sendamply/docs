# Tracking Data

### Control how you track data in your emails

Amply differentiates and tracks messages by taking a hash of the email body which is stored along with the email subject. If you have dynamic content or links in your email, Amply is easily configured to correctly categorize similar emails.

**Links**

The href value of each link is when taking the body hash. This means the following emails will be tracked together:

```json
Subject: How you doin?

<p>Hi,</p>
<p>How is your day going?</p>

<p>Check out your profile <a href="https://ONE.com/profile/1111>here</a>.</p>
```


will be considered the same as:

```json
Subject: How you doin?

<p>Hi,</p>
<p>How is your day going?</p>

<p>Check out your profile <a href="https://TWO.com/profile/2222">here</a>.</p>
```

### Dynamic Content

But what happens if you want to include dynamic data in your emails, but still classify them as the same. You can do this by assigning the class "amply-ignore" to any data you want us to ignore when we hash your email body contents.

For example:

```json
Subject: How you doin?

<p>Hi <span class="amply-ignore">Joey</span>,</p>
<p>How is your day going?</p>

<p>Check out your profile <a href="https://ONE.com/profile/1111">here</a>.</p>
```


will be considered the same as:

```json
Subject: How you doin?

<p>Hi <span class="amply-ignore">Chandler</span>,</p>
<p>How is your day going?</p>

<p>Check out your profile <a href="https://TWO.com/profile/2222">here</a>.</p>
```

This control gives you the ability to easily categorize and group emails how you want, so you can track trends across high level data points.


#### Using Templates

There are several ways you can use templates with Amply.

**Default template**

You can set a default template from your Settings page. This will be used by default in all of the email you send, but can be overriden with the X-SMTPAPI header.

**X-SMTPAPI header**

For more fine grain control, you can specify a template in your transactional email from the X-SMTPAPI header. For more information, check out the X-SMTPAPI docs.
