---
layout: post
title: "Single use disposable tech"
category: "innovation-architecture"
tags:  
author: "Peter Hempsall"
contributors: ""
---

Sometimes we don’t need robust systems… we just need to be able to use powerful tech to get an answer. And then it’s disposed of. Think of this an experiment, redefining what we mean by “experimental tech”.

## Why don’t we traditionally think like this?

Traditional orthodoxy tells us: The cost of building and setting up tech is so high, you’ll only get payback if you build something repeatable.

And so people have got used to all tech being robust and repeatable.

Yes, robustness and completeness still costs money. But the other overheads are dropping rapidly: cloud makes infrastructure provision cheap and disposable. Open source frameworks make building simple “POC” level apps cheap.

But, any professional developer reading this will probably be sweating at this point because they know that the gap between POC and MVP is multiples of cost. And they’ve probably be burnt in the recent past by non-tech specialists assuming the cost to get to the next level of completeness is 10% rather than a more realistic 10x. It’s always 10x.

## So how do we bridge these gaps?

Firstly, we need to understand value. If a “one-shot” answer using tech can give a multiple of return on investment then this approach could work. As a general rule of thumb, aim for a 5x return on investment for tech, because it’s usually harder and more expensive than you thought it would be so this gives headroom to still win.

Secondly, we need to make sure there is a shared understanding of what we’re doing and what the bill payer is buying (even in internal teams, there is always a bill payer). **The output is the deliverable, not the system**. If the bill payer thinks they’re buying a system that will give them repeatable delivery of value over time… then stop: this isn’t the right approach.

Third, we need to think about how underlying tech (the platform, or common core components) and processes (security, ops, billing) can support teams who want to pull off this sort of feat. For example, there is no use making it cheap and easy to build if its expensive and time consuming to get approval to use it!

Finally, we need to accept and commit to disposability. In order to reap the benefits of throw-away, teams need to confidence that they won’t have to support this thing long term. Otherwise they will hedge, and cost and complexity will creep up.

So, some ground rules:

* Make sure everyone is clear on the goal: the output is the deliverable, not the system

* The tech is used to get the result. It is used by the team building it. There are no “users”.

* Given there are no users, there is obviously no external access. Locking down the perimeter really allows the quality and security bar, and therefore cost, to be dropped.

* Once we have an answer, we turn it all off. Sure, you can keep a copy of the code, but expect it to rot within days.

* If you then decide you want a system… then build a system! You can take the learning and knowledge from this experiment, but nothing more.
