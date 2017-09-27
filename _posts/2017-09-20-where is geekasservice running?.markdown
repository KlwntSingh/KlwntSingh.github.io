---
layout: post
title:  "Where is GeekAsService running?"
date:   2017-09-20 12:55:47 -0300
categories: aws, wordpress, devops 
tags: blogging, aws, ec2, cloudfront, rds, deployment, devops, wordpress
---
Hi There! This article will list down the technologies used in **running [GeekAsService.com][website] blog**. 

## Scope
For bringing **[GeekAsService.com][website]** up and running, I tried and used number of different technologies and services. We will discuss these technologies. If anybody is looking for technology stack for running their blog then this is the recommended read for you. 

## General Steps involved in running blog
* Registering for domain name
* Deciding on CMS software to use for blogging
* Deploying CMS software on server

**Registering domain name** is the easiest job from the above-given list. There are number of popular services for registering a domain name like *Hostgator*, *GoDaddy* etc. But for **[GeekAsService.com][website]** domain we used *Bigrock*.  

Next, Deciding on **what CMS software to use** is a time taking task. I wanted to use highly customizable framework/software for blogging. Couple of options available were WordPress, Drupal(both are PHP based), Keystone(Node.Js based) frameworks. Being a beginner, I choose WordPress even though Drupal is highly customizable but its drawback is that it has a learning curve.  

Now, comes the part of **deploying your CMS framework**. There are number of free hosting service providers available which you can search on google. These service providers are very easy to use and deploy WordPress based websites. But for **[GeekAsService.com][website]**, I opted to go with *AWS based infrastructure* and for that, I signed up for AWS free tier service package which is free for 1 year.  
There couple of reasons for choosing AWS services:  
**a.**  I wanted to explore AWS services.  
**b.**  AWS provides services for free for 1 year.  
**c.**  Since Cloud is Hot and trending in the market for deploying enterprise applications.  
**d.**  Complete control over infrastructure.  
**e.**  Application Can be Scaled and expanded according to my needs.

## AWS Services used by <span style="color:#1e60b3">**GeekAsService.com**</span>
* ec2 instance
* MySql RDS instance

 Wordpress application is deployed on an ec2 instance with 1gb of ram and 8gb of disk space. And the database is hosted on Mysql RDS service. AWS provides nice GUI for doing above tasks.

 ## Experimental Things tried with AWS
 * Static IP assignment to an ec2 instance
 * Cloudfront for delivery of Static Resources
 * Deploying WordPress application on cluster
 * ec2 instance load monitoring 
 * Exploring different services like cloud formation and other tools like terraform for maintaining infrastructure as code.

 Front above list, **static IP assignment to an ec2 instance** and **ec2 instance load monitoring** using custom scripts were fairly easy as AWS itself provides provision for doing these tasks.   

 **Cloudfront for delivery Static Resources** worked fine until AWS started charging me for crossing free tier limits of an s3 bucket.  
 ***FYI:-**  s3 bucket is used internally by cloud front for storing static resources.*

#### Currently, I am working on two things  
  * **Deployment of WordPress on the cluster** and staying within free tier limits. The attitude of working in certain limits help explore new ways of doing the same thing.
  * Tools for **maintaining AWS infrastructure as code**.
 
 Hope you find the article useful.

 [website]: https://www.geekasservice.com