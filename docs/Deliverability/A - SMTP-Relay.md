# SMTP-Relay

Sending email through our SMTP relay is the easiest way for an application to use Amply because it only requires updating your SMTP configuration.

1. Change your SMTP username to the username of the Pool or IP Address you want to send from. For most use cases, you should use the Global Pool.
2. Set the SMTP password of the relay to one of your live access tokens.
3. Set the SMTP host of the relay to smtp.sendamply.com.
4. Use port 465 for TLS connections and port 587 or 2525 for plain connections. 587 and 2525 can be made secure by upgrading the connection with the STARTTLS command, which is supported by most mail clients.


> **Frameworks**
> 
> Django
> 
> Laravel
> 
> Node.js
> 
> Ruby on Rails