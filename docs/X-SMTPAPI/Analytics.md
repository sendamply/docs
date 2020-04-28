# What is the X-SMTPAPI header?

You may customize the emails you send via SMTP by using different settings (also referred to as filters) that are defined in the X-SMTPAPI header. These filters will override any default settings you have in the "General Settings" and "IP Addresses" pages.

****

### Analytics

Control what type of analytics data Amply stores for the email you send. The default setting is user.

**Analytics levels**

**none** - do not track analytics for emails or users.

**user** - do not track analytics for emails, but track analytics user.

**all** - track analytics for emails and user.

```json
Example
{
  "filters": {
    "analytics": {
      "settings": {
        "level": "user"
      }
    }
  }
}
```

****

### Bounce notifications

Set an email address to receive bounce notifications on failed sends.

```json
{
  "filters": {
    "bounce_notifications": {
      "settings": {
        "enable": 1,
        "email_address": "email_to_receive_notifications@example.com"
      }
    }
  }
}
```

****

### Clicktracking

Track activity on your links.

In order to track clicks, we rewrite the domain in the URLs of your email to point to c.sendamply.com, record the click, and then redirect to the final URL domain and path. Instead of rewriting to c.sendamply.com, we can rewrite to a domain of your choice provided you set up a CNAME on that domain to point to c.sendamply.com.

```json
{
  "filters": {
    "clicktracking": {
      "settings": {
        "enable": 1,
        "domain": "https://test.yoursitewrapper.com"
      }
    }
  }
}

```

****

### Templates

Wrap your emails in a template. You can get the ID of the template from the URL of the template you want to use. For example, if you want to include the template at https://www.sendamply.com/home/templates/1, then the template ID would be 1.

```json
{
  "filters": {
    "templates": {
      "settings": {
        "enable": 1,
        "template_id": 1
      }
    }
  }
}
```

****

### Unsubscribe groups

Define what group a user manages their subscriptions from. You can get the ID of the group from the URL of the group you want to use. For example, if you want to include the unsubscribe group at https://www.sendamply.com/home/unsubscribe_groups/1, then the group ID would be 1.

```json
{
  "filters": {
    "unsubscribe_groups": {
      "settings": {
        "enable": 1,
        "unsubscribe_group_id": 1
      }
    }
  }
}
```

