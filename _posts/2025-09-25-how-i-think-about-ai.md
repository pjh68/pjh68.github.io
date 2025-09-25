---
layout: post
title: How I’m thinking about AI tooling for software development and why the jury is still out (September 2025 edition)
category: "engineering-management"
tags: engineering, tech, hype, ai
author: "Peter Hempsall"
contributors: ""
---

As an engineering leader, with responsibility for the long-term shaping of a product and engineering organisation, I cannot ignore AI software development tools. But having finally come to terms with the fact that I no longer write code at work or for fun, I’m avoiding going down the rabbit hole of self-experimentation. Instead, I’m enabling and encouraging mass experimentation, at the individual and team level and doing a lot of listening. I’m also looking at the macro outputs: Are teams happier? Are teams more productive over a sufficiently representative  time horizon? And how much is this costing us?

As I go through this, I am having to build my own conceptual understanding of how this bolts together as a system of people and tools. 

Here’s my simplified view of how generative AI for software development works:
- It’s a probabilistic dartboard. It will generate “something”. 
    - If you can tolerate high variance, or you didn’t have a particularly specific outcomes in mind, great.
    - If you want to claim that this tech is great: after all the darts have been thrown, pick your favourite dart, draw bullseye around this dart.
- Prompt engineering can, with variable outcome, coerce the output towards your desired path
    - It may take multiple cycles, taking up valuable time
    - It may not work - you may run out of context window before you’ve bullied it into what you want, it might be unbelievably stubborn and sometimes you get a spectacularly divergent explosion or total loss of context.
- Cognitive biases results in lots of this effort being discounted as one-off costs, either in personal learning or setting up rule files




Of all of this, the assumed one-off costs are my biggest concern - we need to run with this for longer to understand where the split between one-off and ongoing effort lies. 

The data is inconclusive, and even more worrying the self-reported data is inaccurate: [metr](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/)


There is also likely to be significant challenges as code bases scale. We know this is true for software teams today: progress slows as the product gets bigger, and lots of investments teams make is in trying to keep this curve of complexity of change growing as slowly as possible. AI tools seem to be best in green-field settings or making limited, well-scope changes. So AI may, through sloppy application, make the change curve growth rate worse and struggle as it grows.

We also have mass uncertainty on the supply side. Pricing, availability / responsiveness are in flux. The cost/benefit ratio cannot even start to be understood right now.

And so for me, the key questions of “does it actually help?” and “should we change how we organise our teams?” remain fully unanswered. I cannot even, at this stage, predict a trajectory and I believe those that are claiming “it will inevitably…” are picking a version of the future they wish to be true without evidence. And this is probably the no.1 thing that annoys me about the current state of the world: The burden of proof is all backwards with AI. Everyone has such FOMO there is a prevalent belief that AI will be amazing. So now when it’s not amazing it must because we’re holding it wrong?

From an engineering leadership perspective, I am a health sceptic. Experimentation is necessary, but if those experiments fail we will learn and move on. I fundamentally disagree with the position that it is inevitable. 
I have a lot of time for this rage piece: [Where's the Shovelware? Why AI Coding Claims Don't Add Up](https://mikelovesrobots.substack.com/p/wheres-the-shovelware-why-ai-coding)

We’re also seeing something interesting: individuals’ personal journey through the hype curve. Working in a large organisation with a diverse set of engineering teams solving different problems in different contexts means we see this playing out in real-time multiple times a month. People love talking about their AI journeys on Slack…  We also have the per-developer token usage data to back it up (not an entirely accurate picture as doesn’t include out-of-work side projects that a lot of developers do). I don’t think we yet have enough time series data to be confident in drawing conclusions, and we’ve had summer holidays making the data noisy… but right now developers are yo-yoing up, then down, our token usage league table in what appears to be high correlation with their Slack announced drinking of the Kool-aid and then subsequent cooling as their posts contain more caveats… 

My "totally unfair and exagerated for effect" portrait of a developer hype curve journey is something like:
1. Play around with chat based workflows, maybe find useful, maybe not
2. Go all in on something more substantive like Cline or alternatives 
3. Sink a lot of time but be amazed
4. Become evangelical 
5. Tell people they are missing out!
6. Tell people if they aren’t seeing the benefit then their using it wrong
7. Go quiet, token usage drops
8. Start asking about for access to latest frontier models there were released yesterday because that will fix all their issues and get them back on the hype train.

Interesting this fits the existing pattern we’ve seen so many times with new technology hype. There is a curious bias in software development towards abstraction - the thrill of building tools that will built tools so you don’t have to build things yourself. I can’t help but feel this is catching people out. I’m also getting flashbacks to Kubernetes and microservices - yes, both of these are useful technologies when applied to the right situation, but I’ve seen a lot of organisations burned by leaping on the hype through FOMO or CV-driven tech strategy. 

Having said all that negative stuff, I do think there are some things that are sticking:
1. Language guide for experienced developers using a new language. 
2. Replacement for stack overflow. Unsure how sustainable this is.

So it’s a better search engine and personalised technical documentation. Is it sufficient? No, people are still going to go to source material. Does it save the wading and cut through the enshitificaiton of the web? Yes, for now.

If you forced me to make a prediction, right now It’s: Some of this will be helpful tooling. We will see marginal improvements in productivity (approx 10% or less on aggregate) and we will be spending more on tooling. Our total cost base will either go up, or stay around the same. 

So yeah, I’m still in the [fizzling of techno hype]({% link _posts/2025-05-10-techno-hype-fizzle.md %}) camp.
