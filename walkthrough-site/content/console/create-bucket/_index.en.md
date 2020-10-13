---
title: Create Bucket
weight: 15
pre: '<b>c. </b>'
chapter: false
---

### S3

1. Sign in to the AWS Management Console and open the S3 console at https://console.aws.amazon.com/s3/.

{{% notice note %}}
For S3 and Cloudfront there is slightly different configuration depending if the site is a SPA or a traditional layered website with a nested folder setup.
{{% /notice %}}

# Single Page App

2. Very easy setup here. Create a new bucket and call it your domain name (note you can call the bucket anything really for an SPA but for consistency I find it good to use a common naming approach as with regular websites)

![New bucket](images/s3-1.png?width=60pc)

# Traditional layered Site

2. Create a new bucket and call it your domain name.

- For static sites hosted in S3, to be used with cloudfront, the bucket name must match the domain name of the static site.

![New bucket](images/s3-1.png?width=60pc)

3. Allow public access to the bucket

- Got to Permissions
- Block public access
- Uncheck the block all public access checkbox and save

![Make public](images/s3-2.png?width=60pc)

4. Turn on static website hosting

- Go to properties
- Static website hosting
- Select Use this bucket to host a website

![Host Static Website](images/s3-3.png?width=60pc)

{{% notice note %}}
We do need to set bucket policies to decide who can have access to our buckets contents. We will come back to this after setting up our cloudfront distribution.
{{% /notice %}}
