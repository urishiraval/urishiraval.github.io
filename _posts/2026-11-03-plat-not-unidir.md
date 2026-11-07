---
layout: post
title: Building useful Platforms with a team
tags: ['Opinion', 'Philosophy', 'Software Engineering', 'SDLC', 'ABCs']
published: true
---

My perspective on this has always been one of capability driven platforms/systems. If you're building platforms in a team, it's crucial to understand that how you build can't be driven from just one side of the team (the ends of the sides being capability drivers and implementation drivers - or classically Business Analysts and Software Engineers).

# Capability Driver

Analyst type roles typically have their workshops and requirements mining to organise capabilities into features.


They go from "the business needs X" to `X = a + b + c`.


Oftentimes the business doesn't even know that it's `X` they need and this whole process of capability breakdown helps uncover the business reality (and [reality is where dragons go to die](https://urishiraval.github.io/2025/07/15/team-reality-dragons-die/)).


Then these Capability Drivers join the refinement and planning team ceremonies, which serves the flow of knowledge and context.

# Implementation Driver

Once the features are understood in terms of their capabilities the engineers have to bring the implementation context into the feature from the software system/platform context.


Once this is understood - the technical analysis needs to begin.


Here, `a`, `b` and `c` are given substance through the implementation details and technical considerations of the platform. This takes into account the current platform context.


Engineers say `a = 10 + 9 + 8 + 7 + 6`. In a good process - these become implementation tasks that are well understood and aligned with the capabilities defined by the analysts.


If there has been diligence from day 0 - the platform context and the business context are equivalent. If not, misalignments and gaps will emerge, leading to friction and inefficiencies in the implementation process.


In that unfortunate case - it's not:
`a = 10 + 9 + 8 + 7 + 6`


It becomes something like:
`a = 10 + 9 + 8 + 7 + 6 + (-1) + (-2)`


We find things that need to be undone or redone.


(Side note on refactoring - this is often the process of addressing the `(-1) + (-2)` parts, ensuring that the implementation aligns with the intended capabilities without introducing unnecessary complexity when feature `a` arrives)

# It's all about ballance baby

The team act of building platforms and software is all about optimising the balance between capability understanding and implementation execution, and all successful teams have net passionate and intensive drivers from both ends. Unsuccessful ones have an imbalance either way (and in the worst case, in both directions).
 

Any lack of drive from the capability breakdown side results in an ineffective system/platform but with great tech.


Lack of drive from the implementation side results in shit tech that does what it needs to really badly.


Lack of drive from both sides and nothing gets achieved - leading to the worst crime of them all - a shit platform that does nothing.


(A note on greenfield vs brownfield systems: Most greenfield systems when they get more brownfield have a tendency to oscillate - the key is to ensure that the frequency is low and we stabilize more towards the middle.)