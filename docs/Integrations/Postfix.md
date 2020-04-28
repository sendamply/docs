# Integrate Postfix

### Integrate Amply with Postfix

Integrating Amply with Postfix is easy and can be done in just a few minutes.


### Update main.cf

Find your Postfix config file, typically at /etc/postfix/main.cf and add the following:

> smtp_sasl_auth_enable = yes
> 
> smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
> 
> smtp_sasl_security_options = noanonymous
> 
> smtp_sasl_tls_security_options = noanonymous
> 
> smtp_tls_security_level = encrypt
> 
> header_size_limit = 4096000
> 
> relayhost = [smtp.sendamply.com]:587


### Update your credentials

Now you need to specify your credentials in the file /etc/postfix/sasl_passwd (you'll likely need to create it):

> [smtp.sendamply.com]:587 yourAmplyUsername:yourAmplyLiveAccessToken

Next, make sure the file has restricted read and write access only for root, and use the postmap command to update Postfix's hashtables to use this new file:

> $ sudo chmod 600 /etc/postfix/sasl_passwd
> 
> $ sudo postmap /etc/postfix/sasl_passwd


### Restart Postfix

Finally, restart Postfix:

> sudo systemctl restart postfix

Postfix should now be configured to send mail through Amply!


### Troubleshooting

**"No mechanism available" error**

If you receive an error "no mechanism available", you are likely missing some SASL libraries.

Install the missing module dependency using apt-get (i.e., Debian, Ubuntu):

> $ apt-get install libsasl2-modules

Or using a yum (i.e., RedHat, Fedora, CentOS):

> $ yum install cyrus-sasl-plain


### Port 587 is blocked

If port 587 is not working for you, please try 2525 in your postfix config. Some ISP's block email ports in an effort to reduce spam.




