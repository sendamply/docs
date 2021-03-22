# SMTP Relay

Sending email through our SMTP relay is the easiest way for an application to use Amply because it only requires updating your SMTP configuration in 4 simple steps.

1. Set your SMTP username to the username specified in your [General Settings](https://sendamply.com/home/settings/general).
2. Set the SMTP password of the relay to one of your access tokens.
3. Set the SMTP host of the relay to smtp.sendamply.net.
4. Use port 465 for TLS connections and port 587 or 2525 for plain connections. 587 and 2525 can be made secure by upgrading the connection with the STARTTLS command, which is supported by most mail clients.

```ruby
  config.action_mailer.delivery_method = :smtp
  config.action_mailer.smtp_settings = {
    address: 'smtp.sendamply.net',
    port: 587,
    user_name: 'yourAmplySMTPUsername',
    password: 'yourAmplyAccessToken',
    authentication: :plain,
    enable_starttls_auto: true
  }
```