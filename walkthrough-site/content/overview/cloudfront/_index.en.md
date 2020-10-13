---
title: Cloudfront
weight: 10
pre: '<b>b. </b>'
chapter: false
---

Storing your static content with S3 provides a lot of advantages. But to help optimize your application’s performance and security while effectively managing cost, you can also set up Amazon CloudFront to work with your S3 bucket to serve and protect the content. CloudFront is a content delivery network (CDN) service that delivers static and dynamic web content, video streams, and APIs around the world, securely and at scale. By design, delivering data out of CloudFront can be more cost effective than delivering it from S3 directly to your users.

CloudFront serves content through a worldwide network of data centers called Edge Locations. Using edge servers to cache and serve content improves performance by providing content closer to where viewers are located. CloudFront has edge servers in locations all around the world, as you can see from the following map:

![Cloudfront](images/cloudfront-map.png 'Cloudfront')

When a user requests content that you serve with CloudFront, their request is routed to a nearby Edge Location. If CloudFront has a cached copy of the requested file, CloudFront delivers it to the user, providing a fast (low-latency) response. If the file they’ve requested isn’t yet cached, CloudFront retrieves it from your origin – for example, the S3 bucket where you’ve stored your content. Then, for the next local request for the same content, it’s already cached nearby and can be served immediately.

By caching your content in Edge Locations, CloudFront reduces the load on your S3 bucket and helps ensure a faster response for your users when they request content.

In the following illustration, you can see that there are no longer requests traversing the globe to get to our content hosted in an S3 bucket. Instead, requests are routed to the “least latent” Edge Location; that is, the closest in terms of delivery speed. CloudFront then serves cached content quickly and directly to the requesting user nearby, as shown with the green arrows. If the content is not yet cached with an edge server, CloudFront retrieves it from the S3 bucket origin. And because the content traverses the AWS private network instead of the public internet and CloudFront optimizes the TCP handshake, the request and content return is still much faster than access across the public internet.

![Cloudfront](images/s3-and-cloudfront.jpg 'Cloudfront')

But how do we secure our content?
