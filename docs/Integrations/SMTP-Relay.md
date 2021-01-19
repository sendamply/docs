# SMTP Relay

Sending email through our SMTP relay is the easiest way for an application to use Amply because it only requires updating your SMTP configuration in 4 simple steps.

1. Set your SMTP username to the UUID of the IP Pool or IP Address you want to send from.
2. Set the SMTP password of the relay to one of your access tokens.
3. Set the SMTP host of the relay to smtp.sendamply.net.
4. Use port 465 for TLS connections and port 587 or 2525 for plain connections. 587 and 2525 can be made secure by upgrading the connection with the STARTTLS command, which is supported by most mail clients.

```ruby
  config.action_mailer.delivery_method = :smtp
  config.action_mailer.smtp_settings = {
    address: 'smtp.sendamply.net',
    port: 587,
    user_name: '3caac321-f100-4036-a925-a98e7d973669',
    password: '183f1c14bbe59ec64cdc7021692b880503982184147e20daa4e2813d43a69def',
    authentication: :plain,
    enable_starttls_auto: true
  }
```