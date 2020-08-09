# X-SMTPAPI Overview

You can customize the emails you send via SMTP by using different settings that are defined in the X-SMTPAPI header. These filters will override any default settings you have in the "General" page under the Mail Settings tab.

****

### Analytics

The analytics setting allows you to control Clicktracking and Email Categories you want to associate with the email. An Email Category is a way you can group and record analytics for similar types of emails.

| Setting | Type | Example |
-----|-----|
| filters\[analytics\]\[categories\] | Array\[String\] | \["Signup Flow", "User Registration"\] |
| filters\[analytics\]\[clicktracking\]\[settings\]\[enable\] | Integer\[0\|1] | 1 |


```json
{
  "filters": {
    "analytics": {
      "categories": ["Signup Flow"],
      "clicktracking": {
        "settings": {
          "enable": 1
        }
      }
    }
  }
}
```

****

### Substitutions

Substitutions let you create dynamic content for your email. Up to 1,000 substitutions can be processed.

| Setting | Type | Example |
-----|-----|
| filters\[substitutions\] | Array\[Object\] | \[{ "-first_name-":&nbsp; "John" }\] |

```json
{
  "substitutions":[{"-first_name-": "John" }]
}
```

****

### Templates

The templates setting allows you to associate a template with an email.

The template_uuid can either by the UUID of the template you want to use, or an object whose keys are template UUIDs and values are weights (on a scale of 0 to 1). This allows you to do A/B testing with templates.

| Setting | Type | Example |
-----|-----|
| filters\[templates\]\[settings\]\[template_uuid\] | String\|Array\[Object\] | { "d5acb025-aeec-4810-98db-61510cce6af9":&nbsp;0.6, "2dea6e03-6fdc-4302-9102-61b6c278a9a9":&nbsp;0.4 } |
| filters\[templates\]\[settings\]\[enable\] | Integer\[0\|1] | 1 |

```json
{
  "filters": {
    "templates": {
      "settings": {
        "enable": 1,
        "template_uuid": "d5acb025-aeec-4810-98db-61510cce6af9"
      }
    }
  }
}
```

****

### Unsubscribe Groups

The unsubscribe group setting allows you to associate an unsubscribe group with an email. If enabled, Amply will include the List-Unsubscribe header, as well as replace all [unsubscribe link/url special variables.](../Templates/A-Templates-Overview.md#special-variables)

| Setting | Type | Example |
-----|-----|
| filters\[unsubscribes\]\[settings\]\[unsubscribe_group_uuid\] | String | c4a49083-8005-4f29-9a58-b4b9d7542f6d |
| filters\[unsubscribes\]\[settings\]\[enable\] | Integer\[0\|1] | 1 |

```json
{
  "filters": {
    "unsubscribe_groups": {
      "settings": {
        "enable": 1,
        "unsubscribe_group_uuid": "c4a49083-8005-4f29-9a58-b4b9d7542f6d"
      }
    }
  }
}
```

