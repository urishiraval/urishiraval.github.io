---
layout: post
title: Opinion - Api's as Dependencies
tags: ["Software Engineering", "System Design", "API", "Dependency Management"]
published: true
---

A little while back, I came across a beautiful concept on the [Software Engineering Radio podcast](https://se-radio.net/).
The topic was [Managing Dependency Freshness](https://se-radio.net/2023/10/se-radio-587-m-scott-ford-on-managing-dependency-freshness/) which spoke about how we could better manage dependencies within and beyond our software systems.
the concept that caught my attention however, was "Api's as Dependencies".

Here are some thoughts.

# API's

In the ever-evolving landscape of software development, the reliance on external services and functionalities has become a cornerstone for creating robust and feature-rich applications. At the heart of this interconnected ecosystem are Application Programming Interfaces, commonly known as APIs.
APIs play a crucial role in software development by enabling communication and interaction between different software systems. 

## As dependencies

When we talk about APIs as dependencies, it means that a software application relies on APIs to perform certain functions or access specific services. These APIs become dependencies for the application because they are essential for the application to function as intended.
As a mental model, the management of API's have the same problem statements as managing a normal library which is to say that inversion of control becomes your biggest assistant to sane maintenance of API dependencies.

A lot of these are somewhat obvious statements - but no less useful because of it.

# A possible avenue to implement this

Clients. Clients everywhere!

An *api client is probably the easiest key to unlocking inversion of control and enabling controlled versioning. I believe I can make life simpler if - for every Api I build - an 'Api Client' is built with it. The dependant systems should only 'speak' to my api through this Client - which is distributed through a package manager and is well versioned.


**Edits as revised on 13 June 2025**

*When I said 'api client' I really meant API SDK. I think at the time the 'SDK' connection didn't click in my head as "API as a Dependency" was a novel (albeit obvious in hindsight) mental model different from what I used to conceptualize at the time.