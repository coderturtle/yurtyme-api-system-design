---
title: Setup CF Distribution
weight: 20
pre: '<b>d. </b>'
chapter: false
---

### Cloudfront

1. Sign in to the AWS Management Console and open the S3 console at https://console.aws.amazon.com/cloudfront/.

2. Specify a delivery method

- We require a web distribution for our static site

{{% notice note %}}
RTMP is being deprecated at the end of the year so web will be the only optino going forward.
{{% /notice %}}

![Delivery Method](images/cf-1.png?width=60pc)

3. Configure the Origin Settings

- Origin Domain Name:
  The first setting is the Origin Domain Name. Given that this is an origin, where the content will originate, we want to use the S3 bucket we created above. You should see it in the list as an available option.
- Origin Path:
  Unless you have your project inside a folder in your bucket, you will not need to specify an Origin Path as this is identifying if CloudFront needs to point to a specific folder within the bucket.

{{% notice note %}}
For S3 and Cloudfront there is slightly different configuration depending if the site is a SPA or a traditional layered website with a nested folder setup. In cloudfront this is primarily around the Origin Access Identity.
{{% /notice %}}

# Single Page App

- Restrict Bucket Access:
  We want to protect the S3 bucket, so we will restrict bucket access. Select Yes for this option.

- Origin Access Identity:
  If you are following this guide, I am assuming you have no Access Identity setup for this already. Select Create a New Identity and keep the default name (Comment) or rename to make sense for your use. I have never had to rename this in my cases but to each their own.

- Grant Read Permissions on Bucket:
  To apply the new Access Identify permissions to the S3 bucket, you will want to select Yes, Update Bucket Policy. I will show you how to verify this later in this guide.

![Origin Settings](images/cf-2.png?width=60pc)

# Traditional layered Site

For sites setup as static hosting on S3 we need to use a custom origin. For CloudFront to get your files from a custom origin, the files must be publicly accessible and we can't use OAIs. It is possible to restrict access to the buckets using [custom headers](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-overview.html#forward-custom-headers-restrict-access). This is more specialized so for the purpose of this walkthrough we won't use them. (Supplemental section to be added in the future to walk through this process).

- Origin Domain Name:
  The first setting is the Origin Domain Name. For our traditional layered site we want to use the static website hosting endpoint specified in the S3 bucket configuration.

![S3 Config](images/s3_config.png?width=60pc)

![Origin Settings](images/cf-origin-2.png?width=60pc)

4. Configure behavior settings

- Viewer Protocol Policy:
  You should select Redirect HTTP to HTTPS.

- Allowed HTTP Methods:
  The default setting (GET, HEAD) will work for most static sites.

- Compress Objects Automatically:
  You should select Yes to compress objects automatically. This will make the files transmitted smaller thus saving you money.

![Behavior Settings](images/cf-3.png?width=60pc)

5. Configure distribution settings

- Alternate Domain Names (CNAMEs):
  This is where you enter the URL for your project. You can have multiple URLs for CNAMES here but if you used an SSL cert or created one with Certificate Manager, then these URLs should be included on the SSL cert.

- SSL Certificate:
  Select your SSL cert from the drop down.Remember, it is important that the SSL cert contains all the URLs used in the setting above.

- Default Root Object:
  This is typically the index.html file but sometimes the project may use another.

![Distribution Settings](images/cf-4.png?width=60pc)

{{% notice note %}}
For the Default Root Object. This is typically the index.html file but for sites with S3 configured for static hosting we leave this blank.
{{% /notice %}}

![New bucket](images/cf-5.png?width=60pc)

6. When ready hit Create Distribution

![New bucket](images/cf-6.png?width=60pc)

7. Wait for distribution to be deployed.

![New bucket](images/cf-7.png?width=60pc)

### Error Page Redirection

Note to avoid your users getting a NoKeyFound error page when they try and access something on the site that doesn't exist we need to configure our 404 error page on cloudfront. This can either be a custom page or in the case of an SPA redirect back to index.html. We will run through the SPA use case here.

1. With the distribution created, click on the ID of the distribution to get back into the settings. You should see multiple tabs and one of them being Error Pages. Click on Error Pages and then click on Create Custom Error Response.

![New bucket](images/cf-8.png?width=60pc)

10. From here, you need to setup a redirect for 404 handling to ensure your SPA works properly.

- HTTP Error Code:
  You want to customize the 404: Not Found HTTP error code.

- Error Caching Minimum TTL (seconds):
  This is the time-to-live (TTL) which is how long the request will remain cached. For dev, I use a 0 value and for production I personally use a 300 value (5 mins).

- Customize Error Response:
  You will want to set this to Yes, so you can customize the response.

- Response Page Path:
  You will want to redirect the 404 error back to you SPA so you will want to enter /index.html or if your SPA uses something else, enter that here.

- HTTP Response Code:
  You want to return a 200: OK for the response since this is a SPA.

![New bucket](images/cf-9.png?width=60pc)
