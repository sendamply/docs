# Domain Integration

There are a couple of steps you need to complete in order for Amply to send email on behalf of your domain and maximize the deliverability rate for your email.


### Marketing Email

To send marketing email on behalf of your domain, you'll need to verify that you have control of the mailbox you send from. The best way to do this (which will give you the highest delivery rate) is to follow the steps below from the "Transactional Email" section. If you cannot update your DNS records, then you can still verify an individual mailbox by navigating to the campaign page and clicking on "Verify New Email Address". If you complete the steps in the "Transactional Email" section, then you can skip verifying your mailbox.


### Transactional Email

In order to achieve the highest level of deliverability for your email, you'll want to add DNS records that implement SPF, DKIM, and DMARC. Updating these DNS entries should only take a few minutes and can be done by logging into your DNS provider (like GoDaddy, Rackspace, or Route53). If you have any questions, we are happy to walk you through the process. You can contact us here and we'll have one of our engineers help you out.

Once you've updated these records, we recommend that you set up your rDNS (reverse DNS) records. This is especially important for high volume senders and greatly increases your deliverability. The first step is to verify your domain from the verified domain page.

After verifying your domain, you're ready to update rDNS. Navigate to your IP page and click on the IP address you want to update. From the "rDNS" section, select the verified domain you want to send mail from, and then create a unique subdomain. We recommend something like "ip1.yourdomain.com", but it doesn't really matter what subdomain you choose; it just has to be unique and the host part (yourdomain.com) matches your verified domain. Make sure you create a valid A record in your DNS settings that points to the IP address you are configuring:

> NAME ip1.yourdomain.com IN A "1.2.3.4"

Congratulations, you're done setting up your email infrastructure!
