---
layout: post
title: The Scientific Method and Value-based Software Engineering - A novice take
tags: ['Opinion']
published: true
---

Why do we struggle to be excellent engineers in corporate? From my view, talking to quite a few people in the same space as me, I get the impression that, although 'Corporate' is where many innovative solutions come from, a large majority of individuals that I've spoken to have complained and ranted about the amount of friction they've experienced getting something through and out of this machine. This article will attempt to break it down within my immediate and limited context based on my observations (be warned though, this might not be as objective as the title might suggest).

# A reductive explanation of the Scientific Method

This has been around for ages - arguably made popular by someone named [John Dewey](https://en.wikipedia.org/wiki/John_Dewey)[1] who coined the term, though he did not invent the actual method. I personally think the scientific method is so fundamental and intrinsic to establishing a rough understanding of what is real, that it's one of those things that would pop up in any civilization independently (which it has by all indications) in some way or form.

The method is simple, it contains a series of steps that form a loop that can be recursive:

1. Question or Observation
2. Research
3. Hypothesis
4. Testing and Experimentation
5. Analysis of outcome data
6. Interpretation
7. Critique, Review and Refinement

These are pretty straightforward but when done iteratively/recursively they provide a consistent framework that is reliable and simple enough to implement.

# The Software Development Life-cycle (SDLC)

In the spirit of living my 2025 AI enabled life - I took a bunch of articles from various different sources, including major needle movers for how corporate software is build like Amazon, Microsoft and the like, and shoved it into Chat GPT. The prompt I used was this:

```prompt
Analyse the following articles: 

1. https://aws.amazon.com/what-is/sdlc/ 
2. https://github.com/resources/articles/software-development/what-is-sdlc 
3. https://www.microsoft.com/en-us/power-platform/topics/phases-of-the-software-development-lifecycle 
4. https://www.ibm.com/think/topics/sdlc 
5. https://www.atlassian.com/agile/software-development/sdlc 
6. https://www.geeksforgeeks.org/software-engineering/software-development-life-cycle-sdlc/ 
7. https://en.wikipedia.org/wiki/Systems_development_life_cycle 

Create a summary of the SDLC based on all of these articles - add references to everything you write
```

Herewith - the AI generated content:

> [!WARNING] AI Generated Content here
>
>## 1. What Is the SDLC?
>The **SDLC** is a structured, systematic process used by development teams to design, build, deliver, and maintain software efficiently, balancing cost, time, and quality. Its goal is to ensure software meets customer and stakeholder expectations while minimizing risk.  
>([aws.amazon.com](https://aws.amazon.com/what-is/sdlc/), [github.com](https://github.com/resources/articles/software-development/what-is-sdlc), [ibm.com](https://www.ibm.com/think/topics/sdlc), [geeksforgeeks.org](https://www.geeksforgeeks.org/software-engineering/software-development-life-cycle-sdlc/), [en.wikipedia.org](https://en.wikipedia.org/wiki/Systems_development_life_cycle))
>## 2. Common Phases of SDLC
>Most sources identify these core phases, though names and counts may vary:
>### Planning & Requirements Analysis
>- Includes **feasibility study**, stakeholder interviews, cost-benefit analysis, requirement gathering, and documentation (e.g., SRS).  
>([aws.amazon.com](https://aws.amazon.com/what-is/sdlc/), [github.com](https://github.com/resources/articles/software-development/what-is-sdlc), [ibm.com](https://www.ibm.com/think/topics/sdlc), [geeksforgeeks.org](https://www.geeksforgeeks.org/software-engineering/software-development-life-cycle-sdlc/), [en.wikipedia.org](https://en.wikipedia.org/wiki/Systems_development_life_cycle))
>### Design
>- Involves choosing architecture, tools, modularization, UML, data flow diagrams, prototyping, threat modeling. Produces design documentation like SDD or architectural blueprints.  
>([ibm.com](https://www.ibm.com/think/topics/sdlc?utm_source=chatgpt.com))
>### Implementation / Coding / Construction
>- Developers write code following the design specs. Best practices include version control, code reviews, refactoring, and using IDEs or AI tools.  
>([aws.amazon.com](https://aws.amazon.com/what-is/sdlc/), [github.com](https://github.com/resources/articles/software-development/what-is-sdlc), [ibm.com](https://www.ibm.com/think/topics/sdlc), [en.wikipedia.org](https://en.wikipedia.org/wiki/Systems_development_life_cycle))
>### Testing (Acceptance)
>- Conducts unit, integration, system, and user acceptance testing to uncover defects. Increasingly combined with automation and continuous testing, including security checks (DevSecOps).  
>([aws.amazon.com](https://aws.amazon.com/what-is/sdlc/?utm_source=chatgpt.com))
>### Deployment
>- Moves software into production through packaging, configuration, release management, and user training or transition planning.  
>([aws.amazon.com](https://aws.amazon.com/what-is/sdlc/), [github.com](https://github.com/resources/articles/software-development/what-is-sdlc), [ibm.com](https://www.ibm.com/think/topics/sdlc), [en.wikipedia.org](https://en.wikipedia.org/wiki/Systems_development_life_cycle))
>### Maintenance / Support
>- Post-deployment phase: fixing bugs, updates, performance and security monitoring, ongoing improvements. May loop back to earlier phases.  
>([aws.amazon.com](https://aws.amazon.com/what-is/sdlc/), [github.com](https://github.com/resources/articles/software-development/what-is-sdlc), [ibm.com](https://www.ibm.com/think/topics/sdlc), [geeksforgeeks.org](https://www.geeksforgeeks.org/software-engineering/software-development-life-cycle-sdlc/), [en.wikipedia.org](https://en.wikipedia.org/wiki/Systems_development_life_cycle))
>### (Optional) Decommission
>- The system is retired when it reaches end of life.  
>([en.wikipedia.org](https://en.wikipedia.org/wiki/Systems_development_life_cycle?utm_source=chatgpt.com))


Say what you will about AI, it's not too shabby at doing time consuming summaries for meaningless blogs with no purpose except to satisfy an obnoxious engineer's need to spew opinions, lest he explode from holding it in.

I digress.

# Scientific Method vs SDLC

Looking at the common phases of the SDLC that our handy AI tools have given us - these have abstract elements of the scientific method albeit for different goals.

We do `planning and analysis` in the beginning - akin to the `research` stage in the scientific method. We do `design` which has elements of `hypothesis` in it - because we never really can know for certain that the architectural picture we're drawing will match the end implementation. We deal with unknown unknowns and by every good definition of software development - we know that the most useful solutions are the ones that are allowed to deviate from the initial plan for the purposes of making the solution more useful. 

Our `implementation/coding/construction` involves a bunch of testing and experimentation when we write code. Granted, the more you write code and become experienced the less you as an individual need to fundamentally test - which is why I believe that there is a point in your engineering career where you unconsciously write less unit tests until you 're-discover' unit testing and how it can be used to accelerate you, but this is a topic for a different rant. Then we reach `acceptance testing` stages when our Business Analysts do verification on whether the implementation meets the acceptance criteria - which is similar to the `analysis of outcome data` step in the scientific method. Lastly, we have `critique, review and refinement` of the artefact when we `maintain and support` our software based on bug reports, enhancement requests etc from our users.

From this vague mapping of these steps - is it any wonder that Agile as a practice, despite being prone to bastardization, is a good thing for software delivery? Again, this is a conversation for a different article maybe [2].


# Why being excellent seems harder

I believe it's primarily because we don't communicate in a conducive way. As soon as you start on the journey to innovate or 'do the right thing' or prevent technical debt, your world becomes 'science based' rather than 'value based'. Don't get me wrong. There's immense value in all these things we want to do like innovation, optimization and just purely taking more time to not have to cut some corners, it's just much much harder for us to communicate this in so called 'corporate-ese'. When we so these things as software engineers, we back-fill the `question or observation` part in the Scientific method, but we rarely map it to the business case, which is (supposed to be) value based. Corporations don't primarily deal with the Scientific Method, they primarily deal with the Software Product. In this world of ROI and ROE, a person that talks about things in terms of anything else makes themselves susceptible to being left out of the equation. Harsh but I've seen it happen and I don't really blame them - we all work to add value to clients of some form but to the other functions of business, we kind of make it seem that we as Engineers value the software more. To be honest, sometimes we do.

I'll give you a prime example. Try explaining why you need to research using 'Graph Databases' to a non-technical product owner of a law firm to see if you can store related documents in a better way[3]. If you say that graph databases deal with traversals better and are more efficient blah blah blah, you'll oftentimes get nowhere - I can put money on this. If you say you would like to explore ways of storing data so that we can more more quickly, accurately and obviously see what documents might be related, and then go on to explain the business case - this is an easier conversation for your stakeholder to have (note, I'm not saying that it will be easier to get buy-in, I don't really know how to do this yet). The problem here is - it's not an easier conversation for the engineer[4], because business value is something that historically was never a thing 'basement engineers'[5] needed to care about.

# Let's communicate value better - so we can innovate more easily

A lot of us wish we didn't have to think in terms of business. "Just let me code!" or "This new design is so cool! What do you mean you don't see the value in refactoring?!". Unfortunately, it is a necessary evil that we have to learn how to define things in 'business value' terms. The way I think of it is that we tend to communicate in a more smart-casual way then semi-formal and corporate can only deal with semi-formal and higher. 

I always hear complaints about business not 'coming to the party' and I feel my community's frustration but we need to also do better and meet non-technical people half-way. I have a personal belief that you can only complain when you've done everything you possibly can. To be completely honest - I don't think we've done everything we can as software engineers when it comes to communicating the value of software and technical things. I know I haven't at least. Until we get this right - it will always be an us vs them attitude, on both sides, and realistically there aren't any sides to begin with. The only side is the stakeholder/client at the end of the day because that's what determines value and success in corporate.

The reality is, software engineers are no longer 'IT' and product owners and stakeholders are no longer 'Business'. We are one and the same, we just don't always act like it. Yes, there is a definite case to be made that 'Business' needs to give us a 'seat at the table'[6] but there is also a case to be made that 'IT' isn't open to or frankly even prepared to take that seat. We are a large part of the business now, but we have yet to act like it.

This is something that, on a grander scheme, I don't know how to change - I don't have the people skills necessary[7] to maneuver or even understand the complexity of this, but what I can do is attempt to grow and adjust how I personally communicate so that I can make things easier for me and my team. It's stupid difficult - but I can already see the benefits of it.

Hopefully I survive the process but if I don't, there's always my backup plan[8].


**-FIN-**


# References and Asides

[1] Not to be confused with [Melvil Dewey](https://en.wikipedia.org/wiki/Melvil_Dewey), who is probably the one you're thinking about that invented the Dewey Decimal System.


[2] Sheesh, this text is opening a can of worms for me.


[3] I've never had to do this - it's just an example that came to my head, but probably because I've worked with lawyers as an engineer before.


[4] If you're reading this and you're an engineer that disagrees with that statement, well done, I'm genuinely happy for you, but f off, this article isn't for you. Go back to being a rock-star engineer! Shoo!


[5] See the hit British show [The IT Crowd](https://en.wikipedia.org/wiki/The_IT_Crowd)


[6] The best book I've read so far is called 'A Seat at the Table' by Mark Schwartz. It was 1 of 3 books that changed my perception so fundamentally that I felt like a new person after reading it. Highly recommend.


[7] Yes. Hopefully.


[8] For those that don't know me, I have a backup plan for 1 - if AI takes my job, 2 - my software engineering career goes to shit, 3 - I say the wrong thing to the wrong person and I get fired or 4 - some malicious party has a grudge against me and frames me for something irrecoverable. I'll retire early in disgrace and find work making delicious coffee in some obscure part of South Africa. It won't pay much but I can guarantee I'll be so much happier!