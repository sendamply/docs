# Unsubscribe Groups Overview

Unsubscribe groups represent types of email that you send to your users, which they can opt out of. Giving your users a choice to manage what types of email they receive will result in better deliverability with an improved domain and IP reputation.

### Configure

You'll need to specify the unsubscribe group UUID you would like to use whenever you make an API request with our SDK or SMTP relay. You can then include a URL or link in your email body using Handlebars sytax:

|  Name | Description |
|---|---|
| **{{unsubscribe_group_url}}** | This will be replaced with an unsubscribe group url (if the unsubscribe group has been set)   |
| **{{unsubscribe_group_link}}** | This will be replaced with an unsubscribe group link (if the unsubscribe group has been set) |