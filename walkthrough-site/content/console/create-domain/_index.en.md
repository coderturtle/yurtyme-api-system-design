---
title: Create a Domain
weight: 5
pre: '<b>a. </b>'
chapter: false
---

### Route 53

To register a new domain using Route 53

1. Sign in to the AWS Management Console and open the Route 53 console at https://console.aws.amazon.com/route53/.

- If you're new to Route 53, choose Get started.

- If you're already using Route 53, in the navigation pane, choose Registered domains.

2. Choose Register domain, and specify the domain that you want to register:

![Check Domain](images/route53-1.png?width=60pc)

- Enter the domain name that you want to register, and choose Check to find out whether the domain name is available.

- If the domain is available, choose Add to cart. The domain name appears in your shopping cart.

- Choose Continue.

3. On the Contact Details for Your n Domains page, enter contact information for the domain registrant, administrator, and technical contacts. The values that you enter here are applied to all of the domains that you're registering.

![Personal Details](images/route53-2.png?width=60pc)

Choose Continue.

{{% notice note %}}
If the registry requires verification and if it's possible to verify the address during domain registration, the console displays a Verify the Email Address for the Registrant Contact section
{{% /notice %}}

4. Review the information that you entered

![Confirm Details](images/route53-3.png?width=60pc)

- Choose whether you want us to automatically renew your domain registration before the expiration date.
- read the terms of service, and select the check box to confirm that you've read the terms of service.
- Choose Complete Purchase.

{{% notice note %}}
A confirmation email will be sent from noreply@registrar.amazon.com. The registrant contact must follow the instructions in the email to confirm that the email was received, or AWS will suspend the domain as required by ICANN. When a domain is suspended, it's not accessible on the internet.
A hosted zone for the new domain is automatically created for you once the domain is created.
{{% /notice %}}
