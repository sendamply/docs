# Deliverability Strategy

When you set up your verified domain, you’ll be prompted to configure a deliverability strategy. Configuring a deliverability strategy makes sending email easier and more effective. 

There are several deliverability strategies that you can choose from: auto, dedicated, shared, and custom. Auto is the recommended strategy because it learns from your sending activity in real-time to determine the optimal path to reach your user’s inbox - choosing between a shared or dedicated IP and taking the guesswork out of scaling your email infrastructure.

****

### Auto

Auto automatically determines the best strategy (shared or dedicated) depending on your sending habits and volume at any given time. Amply monitors your email infrastructure in real-time and automatically updates to a shared or dedicated strategy if we detect any significant changes to your sending activity. This proactive approach ensures the highest rate of deliverability.

****

### Dedicated

A dedicated strategy is for higher volume senders (> 25,000 emails/month). Since you have already established your domain reputation with mailbox providers, you’ll have no problem building a positive IP reputation. Dedicated IPs are great for high volume senders because they give you full control over your reputation and sending infrastructure. They provide you with a strong foundation as your email volume increases and your deliverability needs grow. 

Keep in mind that if you use auto as your deliverability strategy, Amply automatically determines if dedicated is the best option for you.

****

### Shared

A shared strategy is primarily used for lower volume senders (< 25,000 emails/month). Shared IPs allow you to send email with a positive reputation and high deliverability regardless of volume. A shared strategy can also help high volume senders mitigate deliverability issues from sudden volume spikes. For instance, if we notice an increase in bounces from your dedicated pool due to a short burst in volume, we can temporarily fall back to shared IPs. We’ve built in redundancy by integrating SES with Amply so that your deliverability is always up no matter what.

Keep in mind that if you use auto as your deliverability strategy, Amply automatically determines if shared is the best option for you. 

****

### Custom

A custom strategy load balances traffic between Amply dedicated IPs and a custom SMTP server of your choice. This is a great option if you’re converting to Amply from another provider. It also enables you to use multiple service providers to send your emails for added redundancy. With the custom option, you’ll never be sending out of a shared IP. You’ll either be sending out of your Amply dedicated IPs or through another provider.