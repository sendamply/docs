# Deliverability Strategy

Deliverability strategies improve deliverability and add redundancy for your email.

There are several deliverability strategies that you can choose from: auto, dedicated, shared, and custom. Auto is the recommended strategy because it learns from your sending activity in real-time to determine the optimal path to reach your user’s inbox - choosing between a shared or dedicated IP address and taking the guesswork out of scaling your email infrastructure.

****

### Auto

Auto automatically determines the best strategy (shared or dedicated) depending on your sending habits and volume at any given time. Amply analyzes sending data in real-time (opens, bounces, etc.) to determine how emails should be routed to avoid bounces or ending up in the spam folder. This proactive way of routing email ensures high deliverability during common events like volume spikes or when your IP address gets blacklisted.

****

### Dedicated

A dedicated strategy is for higher volume senders (> 25,000 emails/month). Since you have already established your domain reputation with mailbox providers, you’ll have no problem building a positive IP reputation. Dedicated IPs are great for high volume senders because they give you full control over your reputation and sending infrastructure. They provide you with a strong foundation as your email volume increases and your deliverability needs grow. 

Keep in mind that if you select auto as your deliverability strategy, Amply automatically determines if dedicated is the best option for you.

****

### Shared

A shared strategy is primarily used for lower volume senders (< 25,000 emails/month). Shared IPs allow you to send email with a positive reputation and high deliverability regardless of volume. A shared strategy can also help high volume senders mitigate deliverability issues from sudden volume spikes. For instance, if we notice an increase in bounces from your dedicated pool due to a short burst in volume, we can temporarily fall back to shared IPs. We’ve built in redundancy by integrating SES with Amply so that your deliverability is always up no matter what.

Keep in mind that if you select auto as your deliverability strategy, Amply automatically determines if shared is the best option for you. 

****

### Custom

A custom strategy load balances traffic between Amply dedicated IPs and a custom SMTP server of your choice. This is a great option if you’re converting to Amply from another provider. Amply determines the correct volume to send from each provider in order to maximize your sender reputation, without any extra work from your engineering team.

In addition, a custom strategy lets you leverage multiple service providers to maximize redundancy. With the custom option, you’ll never be sending out of a shared IP. You’ll either be sending out of your Amply dedicated IPs or through another provider.