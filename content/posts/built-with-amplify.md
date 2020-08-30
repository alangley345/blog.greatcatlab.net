---
title: "Built With AWS Amplify"
date: 2020-08-28T12:29:10-04:00
---

Welcome to my newly created blog site run entirely off of Amazon's Amplify service using the Hugo framework and version control hosted on Github. It provides compute to generate the HTML pages from markdown, SSL support, logging and a build pipeline. Learn more about it here, [AWS Amplify](https://aws.amazon.com/amplify/).

In full disclosure I probably spent far too much time investigating the different options avaiable to host a simple static site, but this entire process did give me a chance to look into and research several solutions the AWS offers for serving content.

Originally I had considered hosting a site like this locally but really wanted to utilize the cloud as that is kind of the jumping off point for this site. My first thought was throw this on an EC2 instance at reserve instance pricing. but I dismissed that quickly and looked at containers, specifically the ECS platform. 

These were all appealing in their own ways but were still very much a familar domain and I wanted to get away from IAAS and something that I might be able to accomplish in my homelab. Lightsail was also an option considered since it removed the need to define VPCs, IG and generally deal with the network configuration. But omething like Wordpress wasn't that appealing, and it would probably be less hassle to go with a host like Bluehost that specializes in offering Wordpress sites. 

Then I found documentation released by AWS that included the steps to provison s3 buckets complete with logging with the ability of  Cloudfront to deliver content over HTTPS. [Static site hosted in S3 buckets](https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html). I thought this was simple and affordable enough that it would serve my needs that I would stand this up and began to write the Terraform to implement it. I still needed to decide how I was going to generate HTML and CSS, where I would store pictures and how I would get my source into the buckets. 

While researching different scipts, Travis CI, AWS CodeCommit and Github actions among other things to make this happen, I discovered Amplify. It's serverless and had everything that I was looking for. My only costs are the time to build content, storage and bandwidth serving the content. Even with more posts and views, My hosting costs will be a couple of dollars a month or less for the forseeable future. Although options like [Github Pages](https://pages.github.com/) or [Netlify.com](https://www.netlify.com/) would be free and more than meet my needs, using an AWS platform just made sense in the grand scheme of things. 

