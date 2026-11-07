---
layout: post
title: EDA, Simply Realized
tags: ["Event Driven Architecture", "ABCs"]
published: true
---

I've grown tired of saying EDA and then immediately getting shot down because people think Event-Driven Architecture is just Event Sourcing (which I agree is an implementation pain in the ass most of the time). Herewith is the simplest form of an EDA implementation that the limitations of my skill and experience with them allows for.

# Basic Concepts

## Building Blocks

Let's set the scene of our play. I'm going to define basic concepts from a laymen perspective.

1. Event - an event is a snapshot of current state data indicating a significant checkpoint in time.
2. Port - a dedicated place where events can be placed into and forgotten by the place-er or taken from and forgotten by the port
3. Publisher - something that throws events into a port
4. Subscriber - something that takes events from a port
5. Event Bus - something that joins 2 ports to get events from port A to port B in a discrete way

### A note on the Port and Bus distinction

None of the books on EDA I've read yet have this distinction between the port and the bus itself. I'm not doing this simply to be novel, rather from an implementation perspective, using just a port instead of the entire bus is often what language-level eventing feels like (and behaves like in my experience). Oftentimes, things like callback based eventing doesn't have a tangible buffer and is really just highly-decoupled function chaining. This in itself is useful though, because now even ordinary functions are ports! Thus our event-driven concepts become more easily implementable across different levels of abstraction (at least for me).

## Playing Lego

Putting all these basic building blocks together - here is the simplest form of a conceptual EDA mechanism.

![Most Simple EDA diagram]({{ site.url }}/public/assets/conceptual-eda.drawio.png)

# A little more Depth

### The anatomy of an Event Bus

Let's build an Event Bus from scratch. Remember a Bus is just something that connects 2 ports together - so we automatically have 2 ports, Port A and Port B.


Now for the mechanism between them, let's create a data structure. Note that our definition calls for the mechanism to be discrete. This means that for all input events A the behavior of getting it from one port to another should behave consistently. The simplest form of this is just merely saying that putting n number of events onto Port A will guarantee that n number of events will be available at Port B. Let's keep it simple and do this with a linked list (singly-linked).

Now - when I put an event into Port A, it adds to the back of the linked list. When I read from Port B, it takes from the front of the linked list.

Congratulations - we now have a queue!

This is why we almost always think of 'event queues' when we think of EDA. Not because EDA requires a queue but because EDA requires an Event Bus and the queue is just the simplest data structure that can give you that functionality.

![Event Bus Anatomy]({{ site.url }}/public/assets/event-bus-anatomy.drawio.png)

(This means that if one used `queue()` and `dequeue()` functions one could argue that EDA was already being used. Don't say I told you to this though - I don't want the smoke!).

#### Adding basic some resilience (getting swifty with it)

Let's say that you didn't trust the Producers at port A or the consumers of Port B and each node on the queue - i.e. each event - was extremely critical and you wanted resilience in the form of replaying events in case a consumer effed up.

There are multiple ways of adding resilience.

1. Deadletter queues - make it so that at Port B, each consumer should tell you when their happy/unhappy with processing the event - then instead of just deleting from the main queue, create a separate queue and just move it into there if their unhappy - repeat until their happy with processing it.

![Deadletter Queue Anatomy]({{ site.url }}/public/assets/event-bus-dead-letter-queues.drawio.png)

2. Consumer-orientated read/Log-based queues - instead of removing the node from the queue - give every consumer their own port and let them move their port along the queue (as if on a train track) however they need to. This was made popular by Kafka queues. Each consumer holds their own 'checkpoint' and can reset their checkpoint if they messed up. The checkpoint is the port B of log-based queues.

![Consumer-orientated Read Anatomy]({{ site.url }}/public/assets/event-bus-consumer-checkpoints.drawio.png)

#### The major annoyance of resilient busses - faulty Producer

It's important to understand that a Producer effing up is the most annoying thing to deal with in EDA. If a tree fell in a forest and there is no one who heard it or saw it fall and it completely decomposed - did it even happen at all?

In EDA (as with all software engineering) - if correct logging and monitoring isn't implemented - the tree didn't exist - nothing happened and the work is lost.

### Queues vs Topics

Oftentimes people use these interchangeably. I like to give some rigidity to the concepts to help with the later topic of when to use which thing so bear with me.

A queue is exactly 2 ports with a bus between them, whereas a topic is just a port that has a well-known given name with the goal of organising like events. This intentionally more open definition gives a lot of freedom to stack the building blocks in more configurations.

For example - Azure Eventhubs (a log-based queue) famously doesn't have a native topic implementation - but with a clever use of consumer groups and message filtering - one could (if they so needed) implement a rudimentary grouping of events for a consumer. Like creating a consumer group called "ORDERS" and then a consumer on that group only processes messages with "ORDERS" somewhere in the event data.

It's important to understand this distinction because oftentimes usage of these sort of enterprise solutions like Azure Service Bus or AWS SNS Queues become a lot freer.

Note - in some implementations like Azure Service Bus a Topic acts like something that can accommodate many-to-one Subscribers to Events on the topic. This is not an expansion of the definition of a topic but rather a different implementation that results in that feature. How Azure Service Bus topics work is that you basically create multiple ports called 'subscriptions'. In the background these work similarly to the log-based queues I spoke about above but in tha background it seems like Azure effectively creates multiple copies of the queue, 1 for each subscription (they call this virtual queues - so it's probably not as simple as just duplicating everything - at least I really hope so).


# Notes

Some diagrams created by Gemini cause I'm lazy and AI exists.