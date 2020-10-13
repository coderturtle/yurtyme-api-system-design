---
title: Putting it all together
weight: 20
pre: '<b>d. </b>'
chapter: false
---

So what exactly are we going to build with this architecture.

1. We will use S3 to host all our website artifacts.
2. We will use ACM to generate an SSL cert for our domain.
3. We will create a cloudfront distribution which will read and cache content from our S3 bucket.
4. We will use route53 to route requests to our domain to our Cloudfront distribution.

![All Together](images/all-together.jpeg 'All Together')

For the infrastructure as code section, all code can be found in this [github repo](vhttps://github.com/aws-samples/amazon-cloudfront-secure-static-site).

A detailed walkthrough of each AWS service used, and how it is configured can be found in the Create in the Console section.
