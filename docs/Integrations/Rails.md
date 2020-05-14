---
tags: [integrations]
---

# Ruby on Rails

Integrating Amply with Ruby on Rails is easy and can be done in just a few minutes.

### Configure ActionMailer

You can configure all environments in the config/environment.rb file, or a single environment (development, production, or test) in config/environments/*environment.rb*:

```ruby
Rails.application.configure do
  config.action_mailer.delivery_method = :smtp
  config.action_mailer.smtp_settings        = {
    user_name: 'your_amply_username',
    password: 'your_amply_live_access_key',
    domain: 'yourdomain.com',
    address: 'smtp.sendamply.com',
    port: 587,
    authentication: :plain,
    enable_starttls_auto: true
  }
end
```

That's it! All mail sent by your app will be routed through Amply servers.