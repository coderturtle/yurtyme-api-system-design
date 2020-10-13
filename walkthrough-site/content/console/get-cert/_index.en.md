---
title: Get SSL Cert
weight: 10
pre: '<b>b. </b>'
chapter: false
---

### ACM

To enable SSL on our site we need to get a certificate for the domain. Handily for domains registered through route53 we can use ACM to create the required cert.

1. Sign in to the AWS Management Console and open the Route 53 console at https://console.aws.amazon.com/acm/.

- Click Register Certificate
- Request a public cert

![Register Cert](images/acm-1.png?width=60pc)

2. Specify the domain names for the cert

- Add all subdomains required to the cert. For example domain.com, www.domain.com, \*.domain.com.

{{% notice note %}}
For a root domain like www.domain.com you will need both domain.com and www.domain.com on the cert.
{{% /notice %}}

![Add Domains](images/acm-2.png?width=60pc)

3. Validate you own the domain

- Choose how you wish to validate the domain. The easiest option is to use DNS validation.
- With this approach you need to add some DNS values to your route53 hosted zone.

![Validate Domains](images/acm-3.png?width=60pc)

4. Add tags to the cert

![Add Tags](images/acm-4.png?width=60pc)

5. Review the cert details

![Review](images/acm-5.png?width=60pc)

6. Validate the domain

- We chose earlier to validate the domain using the DNS method
- This is made super easy in the console as we are using route53.
- Expand each subdomain
- Click Create record in Route 53
- The records are added for you

{{% notice note %}}
Alternatively you can go into the hosted zone in Route53 and add the CNAME values yourself.
{{% /notice %}}

![Validate](images/acm-6.png?width=60pc)

7. Wait for AWS to validate domain and issue the cert

- This can take up to 24 hours but normally happens in a couple of minutes.
- Once completed the status wil be set to issued.

![Validate](images/acm-8.png?width=60pc)
