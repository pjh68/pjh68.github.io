---
layout: post
title: "The past, present and future of Multi-Tenancy - Part 3: The Future"
category: "software-architecture"
tags: engineering
author: "Peter Hempsall"
contributors: ""
---

This is the third post in a 3 part series about the past, present and future of multi-tenancy architectures for enterprise software products. I am a strong believer that understanding where we have come from, and how we got here, helps us predict where are going.

This post continues the story from [Part 2]({% link _posts/2023-04-06-multi-tenancy-the-present.md %})

# Part 3: The Future

## Where we left the story... 
In part 2, I described how we've already broken the production singleton pattern, moving customer isolation down the stack so everyone has their own prod. Along with security isolation, this also gives us performance isolation and automatic per customer cost visibility. 

Again, context is important here: we’re talking about B2B enterprise applications that are fairly involved, both in terms of sales and implementation. This aren’t sign-up online, instant access, free tier type products. We are talking 10s-100s of new customer per year, not 1000s per day.

## Which cloud?
Salesforce, the daddy of enterprise SaaS, used to have a really simple offering: come to Salesforce.com and we take care of everything. The customer didn't need to concern themselves with worrying about hardware, capacity provisioning or software updates. The first cracks in this are now emerging: Salesforce is giving their customer choice (!!!) of which hyperscale, and which region, they want their instance of Salesforce running on.

SAP has made a similar shift from S4 on SAP Cloud to S4 on "whatever hyperscaler you choose". History may judge them kindly on just how quickly they dropped SAP Cloud, effectively skipping a step on the evolution.

Interesting to note the these giants have both opted to prioritise portability across clouds over cloud native features. Which makes sense - whilst they've accepted the writing on the wall that they're not hyperscalers, strategically they don't want to be beholden to any particular hyperscaler. This strategic choice won't apply to all companies.
## Whose cloud is it anyway?
What is interesting in the Salesforce case is whilst it's on "public cloud" infrastructure, it's not in the customer own cloud account. So the customer has some choice but they don't get the keys to kingdom. This gives a bunch of advantages: Salesforce is still responsible for updates and managing the underlying infrastructure, but in an enterprise landscape the customer may (your own diligence is recommended) get lower ingress/egress charger and lower latency with their other cloud hosted applications. 

But I do see a future (because customers have asked for it) where the customer does control the keys to the kingdom. We've already made them their own isolation prod account on AWS. They're an AWS customer. They're pretty happy with how they manage their AWS accounts and would quite like as much as possible to be within their security control. Let's call this customer-own-cloud.

The challenges here are plentiful:
 - Layer zero guardrails. Enterprises love to add restrictions on what they allow themselves to do in cloud accounts. It's hard to argue with this, especially when cloud vendors leave so many foot-guns lying around. The problem in that every company's layer zero is slightly different. So something that deploys fine in a "raw" cloud account may not work without manually negotiating a number of exceptions with a IT team.
 - Monitoring. We've gotten use to knowing how our applications behave in production and proactively dealing with issues before user's are impacted. This is still possible, but now harder.
 - Deployment. See below.
 
These challenges are technically manageable, but "their cloud, their rules" means a negotiated technical approach is likely... and then you've lost standardisation of your product and processes... eeek.

So maybe just give the problem to the customer if they want it in their cloud?

## The return of packaged software?
OMG, this looks familiar! Flashbacks to the 90s. Software on a CD? In a printed box? Obviously not, but there aren't any established standards for packaging a cloud native application for deployment by another organisation.

Git access and a copy of a pipeline might be a tempting option. Are we essentially back to writing our own Win95 installers?

## The re-rise of the app store?
Cloud app stores do exist. But right now they seem to be little more than directories / marketplaces rather than the full end-to-end discovery-to-installation we see in the consumer app store space.

Just looking at AWS marketplace, it lists acceptable delivery methods as: Amazon Machine Image, CloudFormation Stack, Container Image, Helm Chart, Add-on for Amazon EKS, "Professional Services" (manhandle it into your account?), and SaaS.

I would love to see more progress in this area from the cloud vendors.

## The cost of everything and the value of nothing
This also has some interesting commercial implications for cloud usage and costs. A growing number of applications have an underlying cost base that is highly variable on usage - e.g. optimisation products, anything using a LLM. The go-to enterprise SaaS pricing playbook of per user per month is ill suited to these use cases. 

We all want pricing to be a proxy of value created, but do we really just want to be adding a margin on top of cloud compute costs? On the flip side, if we, as software developers, are no longer responsible for cloud costs, are we then disincentivised to optimise these? I feel enterprise sysadmins from the 90s-00s have already been here and had those arguments!

## Can we conclude anything? Is this inevitable? 
Just because you can do something, it doesn't mean you should!

 At the time of writing (2024) this is true of customer-own-cloud. The shift of responsibilities and the implications on both operations and commercials are many fold. 
 
 There is a lot of detail to shake out, and we have not yet seen a repeatable set of patterns emerging - and this post has been sitting in my drafts for 2 years. I guess that's why this is still the future. 

