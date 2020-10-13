---
title: Solution Details
weight: 10
pre: '<b>b. </b>'
chapter: false
---

### S3 configuration

This solution creates an S3 bucket that hosts your static website’s assets. The website is only accessible via CloudFront, not directly from S3.

### CloudFront configuration

This solution creates a CloudFront distribution to serve your website to viewers. The distribution is configured with a CloudFront [origin access identity](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html) to make sure that the website is only accessible via CloudFront, not directly from S3. The distribution is also configured with a [Lambda@Edge function](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-at-the-edge.html) that adds security headers to every response.

### ACM configuration

This solution creates an SSL/TLS certificate in ACM, and attaches it to the CloudFront distribution. This enables the distribution to serve your domain’s website using HTTPS.

### Lambda@Edge configuration

This solution creates a Lambda@Edge function that’s triggered on an [origin response event](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-cloudfront-trigger-events.html). The function adds security headers to every response served by CloudFront.

The security headers can help mitigate some attacks, as explained in this blog post: [Adding HTTP Security Headers Using Lambda@Edge and Amazon CloudFront](https://aws.amazon.com/blogs/networking-and-content-delivery/adding-http-security-headers-using-lambdaedge-and-amazon-cloudfront/). Security headers are a group of headers in the web server response that tell web browsers to take extra security precautions. This solution adds the following headers to each response:

- [Strict-Transport-Security](https://infosec.mozilla.org/guidelines/web_security#http-strict-transport-security)
- [Content-Security-Policy](https://infosec.mozilla.org/guidelines/web_security#content-security-policy)
- [X-Content-Type-Options](https://infosec.mozilla.org/guidelines/web_security#x-content-type-options)
- [X-Frame-Options](https://infosec.mozilla.org/guidelines/web_security#x-frame-options)
- [X-XSS-Protection](https://infosec.mozilla.org/guidelines/web_security#x-xss-protection)
- [Referrer-Policy](https://infosec.mozilla.org/guidelines/web_security#referrer-policy)

For more information, see [Mozilla’s web security guidelines](https://infosec.mozilla.org/guidelines/web_security).
