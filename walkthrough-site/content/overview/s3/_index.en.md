---
title: S3
weight: 5
pre: '<b>a. </b>'
chapter: false
---

The first step is to store your content in a secure and scalable way. A simple and flexible approach for static content that you want to make available on the internet is to store it in an Amazon S3 “bucket.” S3 is easy to set up and use, and is designed to store and retrieve any number of files or objects from anywhere on the internet. It’s simple to use and offers durable, highly available, and scalable data storage at low cost.

When you put your content in an S3 bucket in the cloud, a lot of things become much easier. First, you don’t need to plan for and allocate a specific amount of storage space because S3 buckets scale automatically. In addition, because S3 is a serverless service, you don’t need to manage or patch servers that store files yourself; you just put and get your content. Finally, even if you require a server for your application (for example, because you have a dynamic application), the server can be smaller because it doesn’t have to handle requests for static content.

However, lets take a look at the scenario shown in the following illustration. We’ve stored our content in an S3 bucket located in a region in Europe, and we have users located around the world who access that content. As the arrows show, whenever a user requests content, the request must go over the public internet to the source location–the S3 bucket in Europe. Depending on the user’s location, this can take a long time. The delays might even cause some user requests to bounce and return an error from the page.

![S3](images/s3-serving-content.jpg 'S3')

This is where Cloudfront comes in...
