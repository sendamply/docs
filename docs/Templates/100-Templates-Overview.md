# Templates Overview

Templates wrap email contents in a structured manner.

A template defines the surroundings of an HTML email. It's the place to define a common look and feel of your final output. You can define common headers, footers, etc to your email.

****

### Special Variables

There are several special variables that you may use in your templates. These can be referenced using standard Handlebars syntax.

|  Name | Description |
|---|---|
| **{{subject}}** | This will be replaced with the email subject. |
| **{{body}}** | This will be replaced with the email body. |
| **{{unsubscribe_group_url}}** | This will be replaced with an unsubscribe group url (if the unsubscribe group has been set)   |
| **{{unsubscribe_group_link}}** | This will be replaced with an unsubscribe group link (if the unsubscribe group has been set) |