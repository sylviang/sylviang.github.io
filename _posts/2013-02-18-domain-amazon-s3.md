---
layout: post
type: text
title: Point domain to Amazon S3 bucket 
date: 2013-02-18 21:52:00
---

I've recently registered a domain name ([sylviang.me](http://sylviang.me)) from Media Temple benefiting from their $1 valentine's day domain sale. So I decided to "live" this blog that I've been working on for the past few days. 

Setting up an S3 bucket as a static website is pretty straightforward as referred to the [AWS guide](http://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html). However, as this is the 1st time I am using Amazon S3 and Media Temple DNS, I am not sure how should I configure my DNS. But nothing is not possible with some googling and playing around. 

For clarity sake and because I'll forget if I don't write it down, I am going over the steps below. 

1. Create two buckets. It must be the same name as your domain name. e.g. sylviang.me & www.sylviang.me

2. Upload your content to one of the S3 bucket (sylviang.me). 

3. Configure buckets for website hosting. Enable website hosting for bucket (sylviang.me). Redirect all requests to another host name for bucket (www.sylviang.me).

5. Test and make sure the "EndPoint" url works as expected. It should be something like sylviang.me.s3-website-ap-southeast-1.amazonaws.com 

6. Using the administration tools provided by your domain registrar, remove any "A" records that may have been automatically setup for your domain.

7. Forward your root domain (sylviang.me) to the www subdomain (www.sylviang.me). Mask the forwarding so visitors will see your registered domain instead of the S3 url.

8. Add a "CNAME" for the www subdomain, pointing to your S3 url (sylviang.me.s3-website-ap-southeast-1.amazonaws.com).

9. Now wait for the changes to propagate!