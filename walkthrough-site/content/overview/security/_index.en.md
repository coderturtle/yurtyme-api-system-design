---
title: Security
weight: 15
pre: '<b>c. </b>'
chapter: false
---

Often, companies that distribute content over the internet want to restrict access to documents, business data, media streams, or other content so that only selected users, like paying customers, can request it. By using CloudFront, we can set up additional access restrictions like geo-restrictions, signed URLs, and signed cookies, to further constrain access to the content following different criteria.

Another security feature of CloudFront is Origin Access Identity (OAI), which restricts access to an S3 bucket and its content to only CloudFront and operations it performs. The CloudFormation template in final section of this walkthrough includes OAI to help ensure that your content is protected and restricted.

![OAI](images/oai.png 'OAI')

CloudFront includes additional protection against malicious exploits. To provide these safeguards, CloudFront integrates with both AWS WAF, a web application firewall that helps protect web applications from common web exploits, and AWS Shield, a managed DDoS protection service for web applications running on AWS. AWS WAF lets you control access to your content, based on conditions that you specify, such as IP addresses or the query string value on a content request. CloudFront then responds with either the requested content, if the conditions are met, or with an HTTP 403 status code (Forbidden). All CloudFront customers benefit from the automatic protection of AWS Shield Standard, at no additional charge. But customers who want deeper insights, enhanced mitigations, and cost protections against DDoS attacks can use AWS Shield Advanced.
