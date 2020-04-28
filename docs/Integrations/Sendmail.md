# Integrate Sendmail

### Integrate Amply with Sendmail

Integrating Amply with Sendmail is easy and can be done in just a few minutes.


### Authorization

Set the authorization credentials in /etc/mail/access:

> AuthInfo:smtp.sendgrid.net "U:yourAmplyUserName" "P:yourAmplyLiveAccessToken" "M:PLAIN"


### Update your config

Define the Smart Host in /etc/mail/sendmail.mc:

> define(`SMART_HOST', `smtp.sendamply.com')dnl
> FEATURE(`access_db')dnl
> 
> define(`RELAY_MAILER_ARGS', `TCP $h 587')dnl
> 
> define(`ESMTP_MAILER_ARGS', `TCP $h 587')dnl

Next, update sendmail.cf and access.db files (you will need to run these commands as 'su' or 'root'):

> $ cd /etc/mail
> 
> $ m4 sendmail.mc >sendmail.cf
> 
> $ makemap hash access < access


### Restart Sendmail

On older distros, you can run restart sendmail like so:

> $ /etc/init.d/sendmail restart

On newer versions, restart with:

> $ service sendmail restart

Sendmail should now be configured to use Amply!



