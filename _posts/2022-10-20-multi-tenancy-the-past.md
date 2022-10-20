---
layout: post
title: "The past, present and future of Multi-Tenancy - Part 1: The Past"
category: "software-architecture"
tags: engineering
author: "Peter Hempsall"
contributors: ""
---

This is the first post in a 3 part series about the past, present and future of multi-tenancy architectures for enterprise software products. I am a strong believer that understanding where we have come from, and how we got here, helps us predict where are going.

# Part 1: The Past

Multiple end users having isolated access to their data in a shared system is almost as old as computing itself. The first demonstration of a shared system of notable scale was back in 1961 with the [Compatible Time Sharing System at MIT](https://multicians.org/thvv/compatible-time-sharing-system.pdf).

But these were generally users of the same organisation. And the organisation itself ran its own copy of the software on its own hardware. That started to change around the turn of the 21st Century, with the birth of Software-as-a-Service. 

Salesforce claims to be the first proper enterprise-scale multi-tenanted architecture - [the company was founded in 1999 and the product launched in 2000](https://www.salesforceben.com/salesforce-history/). But outside the enterprise space, one could consider Hotmail (launched in 1996) was an even earlier example of SaaS.

To understand just how big a siesmic shift SaaS was, we need to remind ourselves of the state of enterprise IT at this point in history. The journey from wanting some new software to using it was long and tortuous. First someone had to work out how much hardware was needed to run the software. Then they'd have to work out where to put this hardware and how to plug it in. Then they'd need to buy it, build it and plug it in. Don't forget, it wasn't until 2006 that AWS launched with S3 and EC2 as its first services. After the hardware was sorted then the fun of actually installing the software could begin.

According to Salesforce's marketing, it was the installing software part of the journey that people really hated. Their "no software" logo was a pervasive presence. They even had someone dress up as a fluffy mascot version of it at their Dreamforce events. I always thought "no hardware" was the stronger point and technically more accurate, especially given the amount of custom apex code a typcial enterprise Salesforce customer had running in their tenant! 

So here was the promise of SaaS: immediately available, don't worry about the hardware or installing any software or indeed any future upgrades. All that would be handled by the SaaS provider. And they would run your workloads and store your data alongside all their other customers... but use ~~magic~~ clever engineering to keep it all logically seperate. 

What's not to love? Well... throughout the history of shared systems, the major concerns of paying customers and end user haven't really changed. It boils down to two things:
 - Security isolation: only I should see my data. I shouldn't see others' data.
 - Peformance isolation: my workload shouldn't be impacted by others (the "noisy neighbour" problem)


These concerns don't just apply to SaaS - the same challenges befall any shared system, be it IaaS, PaaS or SaaS. 

So how did what I'm going to call the "2000-2020 era SaaS products" address these concerns? Let's tackle them one at a time.

## Security
The basic approach to security is to stick a "CustomerID" column on every table in the database and then filter on that. Simple.

Except all the ways it can go wrong... and plenty of companies (including banks) have been caught with their trousers down through some common pitfalls:
 - if every query now needs a CustomerID, you are only one badly written SQL statement away from missing this somewhere
 - caching, already hard, now becomes even harder 
 
Generally, good practice is to isolate the logic as low in the stack as possible. In the data access layer (e.g. ORM), or even enforced at the database. 

It almost goes without saying that cross-account vulnerabilities have kept many a hacker entertained for hours.


## Performance
In reality, big SaaS products ended up sharding their customers over multiple instances. But how to manage contention within an instance?

Salesforce is again an interesting example. Their approach is to quantize work and brutally enforce limits. This way, no large blocking requests can take down the system for other users. Timeouts are ruthlessly enforced. Back when I was a salesforce developer, the limits guide was always open on my laptop. Want a query that returns 50,000 records? Fine. Want to return 50,001? Over Salesforce’s dead body!

IaaS providers take a similar limits based approach for many of their cloud-native services (e.g. AWS Lambda). AWS's playbook is to launch a new service with quite tight limits, and expand those limits as they get more confident managing bigger workloads without contention. 

For virtual machines (e.g. AWS EC2), noisy neighbours have been a common complaint for years. The solution appears to probability: have a large scale and randomly allocate virtual machines to hosts. This lowers the chance of being on a host with lots of noise neighbours. It's still a risk, and a number of people have developed tactics to detect performce-degraded hosts and to re-roll the dice by spinning up a new machine. 


## Summary
This history takes up to around 2014... we have stopped just short of the next major technical milestone: the leap from reproducable builds to infrastructure-as-code and reproduceable environments. 

Part 2 will cover what this leap enables... 

