# Sender Verification

To maximize deliverability and protect the security of our customers, we require you to verify your sending domain. Domain Verification requires you to configure your DNS records ([SPF](./200-SPF.md), [DKIM](./300-DKIM.md), and [DMARC](./400-DMARC.md)) which greatly improves the deliverability of your sending infrastructure.

****

### Domain Verification

In order to verify your domain, you need to create DNS records that implement [SPF](./200-SPF.md), [DKIM](./200-DKIM.md), and [DMARC](./400-DMARC.md) with the appropriate Amply resources. Once verified, you may send email on behalf of your root domain or subdomains.

Navigate to the [Verified Domains](https://sendamply.com/home/settings/verified_domains) page from the Mail Settings tab on your dashboard and click on the "+" button to create a new Verified Domain. You'll be prompted to add the following DNS records for the domain (in this example, `yourdomain.com`):

![Verified Domains](../../assets/images/verification.png)

|  Name | Reason |
|---|---|
| **amp.yourdomain.com**  | This is used to set the return-path of your email. Additionally, email clients use this for SPF authentication. |
| **amp._domainkey.yourdomain.com**  | This is used by email clients for DKIM authentication. |
| **c.amp.yourdomain.com** | This is used for clicktracking and our tracking pixel to collect analytics. |
| **_dmarc.yourdomain.com** | This is your DMARC policy and instructs email clients how to respond if an email fails SPF or DKIM authentication. We recommend you set your policy to _quarantine_ or _reject_, but you may set it to _none_ if you are unable to enforce a policy. |

<!-- theme: info -->
> We have found that setting a DMARC policy to _quarantine_ or _reject_ greatly improves the deliverability of your email with popular email clients like Gmail and Outlook.
>
> Learn how to safely enforce your DMARC policy [here](./400-DMARC.md#safely-transitioning-to-an-enforced-dmarc-policy).

#### Resources to update records for popular DNS providers

- [AWS Route53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resource-record-sets-editing.html)
- [GoDaddy](https://www.godaddy.com/help/add-a-cname-record-19236)
- [Google Cloud](https://cloud.google.com/dns/docs/records)
- [Rackspace](https://support.rackspace.com/how-to/creating-dns-records-with-cloud-dns/)

#### Add your domain

Once you've provisioned your DNS records, you'll see green checkmarks indicating that the records have been set up correctly. Click on "Create", and you've completed the verification process and will be able to send email on behalf of your new domain!