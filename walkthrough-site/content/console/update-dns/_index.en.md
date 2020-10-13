---
title: Update DNS entries
weight: 30
pre: '<b>f. </b>'
chapter: false
---

### Route53

Finally we need to update the DNS records to point the domain name to the Cloudfront distribution.

1. Sign in to the AWS Management Console and open the S3 console at https://console.aws.amazon.com/route53/.

- Click on Hosted Zones
- Select your sites domain.
- Click on Create Record Set

2. We need to create our IPV4 record sets

{{% notice note %}}
We need to setup 2 record sets. One for www.yourdomain.com and a second for yourdomain.com
{{% /notice %}}

- Name: www
- Type: A- IPv4 address
- Alias: Yes
- Alias Target: Select the Cloudfront distribution we created earlier
- Click Create

Repeat for the non www root domain

- Name: {leave blank}
- Type: A- IPv4 address
- Alias: Yes
- Alias Target: Select the Cloudfront distribution we created earlier
- Click Create

![Public Policy](images/ipv4.png?width=60pc)

3. We need to create our IPV6 record sets

{{% notice note %}}
We need to setup 2 record sets. One for www.yourdomain.com and a second for yourdomain.com
{{% /notice %}}

- Name: www
- Type: AAAA - IPv6 address
- Alias: Yes
- Alias Target: Select the Cloudfront distribution we created earlier
- Click Create

Repeat for the non www root domain

- Name: {leave blank}
- Type: AAAA - IPv6 address
- Alias: Yes
- Alias Target: Select the Cloudfront distribution we created earlier
- Click Create

![Public Policy](images/ipv6.png?width=60pc)

{{% notice note %}}
Note it can take anywhere from a few seconds to 24 hours for the DNS updates to propogate.
{{% /notice %}}
