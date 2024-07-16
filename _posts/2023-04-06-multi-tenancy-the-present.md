---
layout: post
title: "The past, present and future of Multi-Tenancy - Part 2: The Present"
category: "software-architecture"
tags: engineering
author: "Peter Hempsall"
contributors: ""
---

This is the second post in a 3 part series about the past, present and future of multi-tenancy architectures for enterprise software products. I am a strong believer that understanding where we have come from, and how we got here, helps us predict where are going.

This post continues the story from [Part 1]({% link _posts/2022-10-20-multi-tenancy-the-past.md %})

# Part 2: The Present

## Where we left the story... 
This history takes us up to around 2014... we have stopped just short of the next major technical milestone: the leap from reproducible builds to infrastructure-as-code and reproducible environments. 

But the headline remains the same: Our major worries are still security isolation and performance isolation beween tenants.

Context is important here: we’re talking about B2B enterprise applications that are fairly involved, both in terms of sales and implementation. This aren’t sign-up online, instant access, free tier type products. We are talking 10s-100s of new customer per year, not 1000s per day.

## Infrastructure-as-code revolution
I may be slightly over enthusiastic about this, but I believe that infrastructure-as-code was a pivotal moment for our industry. It was the tooling that unlocked the true potential of cloud computing.

Used right, standing up a new environment is a couple of clicks. Baring cost (see below), everyone can now have as many environments as they want. Our QA team love that they can have multiple short-lived environments. 

And because creating new environments is now regularly exercised, we can have confidence that any disaster recovery plans that depend on this step will work.

## Scale to zero
Environments may carry a cost, even when not doing anything useful. Some services have hefty standing charges for existing, which can add up. So we care deeply about how well costs scale down. Ideally, costs should scale down to zero when not used. AWS Lambda is a good example of this. 

This isn't because we're cheap. I'll happily direct a team to spend more on infrastructure to solve problems (and our AWS bill is a testament to that).

The reason for caring aout scale-to-zero is that it brings freedom. I have seen too many examples of teams bringing in convolutions to their environment plans to compensate for high fixed costs. This leads to leaking of concerns (e.g. performance contention, security risks) and a whole world of additional admin. For most teams, I don't believe worrying about how well they can pack and utilise a particular services is a good use of their time. So we explicitly favour scale-to-zero architectures. 

## Environment isolation (account/subscription mapping)
One side note, that is worth mentioning. Cloud accounts (or subscriptions, depending on your cloud provider's terminology) can carry an overhead. We tend to therefore cluster multiple environments inside an account. But we do use accounts as our highest level of isolation. 

## Break to Production singleton pattern
From here, it's a small logic leap to realise:
1. There is nothing that says we only need to have one Production environment
2. We have everything we need to create Production environments on demand

So now we have more options of just how far we can shove the customer access logic down in the stack. The logical end point: cloud account level isolation. 

We can now remove mutli-tenant logic from our application, and with it a whole class of security risks. 

This also bring two other automatic benefits: performance isolation AND automatic per-customer cost visibility.

This is the present we are living in.

## Where next?
[Part 3]({% link _posts/2024-07-16-multi-tenancy-the-future.md %}) covers the future. The near future. Specifically where I believe B2B enterprise software products are heading, the pitfalls and challenges on the way, and what needs to be true for this to become a reality.




