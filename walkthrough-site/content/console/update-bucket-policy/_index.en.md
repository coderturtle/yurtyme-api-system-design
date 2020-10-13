---
title: Update Bucket Policy
weight: 25
pre: '<b>e. </b>'
chapter: false
---

### S3

1. Sign in to the AWS Management Console and open the S3 console at https://console.aws.amazon.com/s3/.

- Go to Permissions
- Go to Bucket Policy

{{% notice note %}}
For S3 and Cloudfront there is slightly different configuration depending if you are using Origin Access Identifiers on a private bucket or are using the S3 static hosting feature on a public bucket.
{{% /notice %}}

# Single Page App

2. If you walked through the previous CloudFront distibution setup and selected it to update the bucket policy you will have a policy that looks something like this

```yaml
{
  'Version': '2008-10-17',
  'Id': 'PolicyForCloudFrontPrivateContent',
  'Statement':
    [
      {
        'Sid': '1',
        'Effect': 'Allow',
        'Principal':
          {
            'AWS': 'arn:aws:iam::cloudfront:user/CloudFront Origin Access Identity ORIGIN_ACCESS_ID',
          },
        'Action': 's3:GetObject',
        'Resource': 'arn:aws:s3:::BUCKET_NAME/*',
      },
    ],
}
```

The problem here is if an object does not exist in the bucket, even with the 404 error page redirect, you will see the error NoSuchKey. This is common for endpoints like /about. This is actually a known issue and is clearly defined in the [knowledge center](https://aws.amazon.com/premiumsupport/knowledge-center/404-error-nosuchkey-s3/). The fix is very simple but unless you understand how these policies work, you will miss this. You need to add the action s3:ListBucket. This sounds easy enough but what gets most people is that this works on a different resource than the s3:GetObject so simply adding the action will not work.

To fix this, update your policy to:

```yaml
{
  'Version': '2008-10-17',
  'Statement':
    [
      {
        'Sid': 'AllowCloudFrontOriginAccess',
        'Effect': 'Allow',
        'Principal':
          {
            'AWS': 'arn:aws:iam::cloudfront:user/CloudFront Origin Access Identity ORIGIN_ACCESS_ID',
          },
        'Action': ['s3:GetObject', 's3:ListBucket'],
        'Resource': ['arn:aws:s3:::BUCKET_NAME', 'arn:aws:s3:::BUCKET_NAME/*'],
      },
    ],
}
```

![SPA Policy](images/s3-policy-spa.png?width=60pc)

# S3 Hosted Site

2. Make sure that public read is allowed on objects in the bucket.

![Public Policy](images/s3-policy.png?width=60pc)
