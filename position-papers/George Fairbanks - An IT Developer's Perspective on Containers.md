# An IT Application Developer's Perspective on Containers

Position paper for: SATURN 2016 Workshop on Containers  
George Fairbanks  
17 April 2016  


## Introduction

Since I've been an IT application developer for most of my professional career (about 20 years) and have sat on the sidelines admiring and studying the work of the "systems developers", my position paper describes a personal account of a few trends I've witnessed regarding how IT applications are built and how containers have affected the trends.  

The first trend involves IT and "systems".  In the early days of application development, computing resources were scarce so all problems were systems problems where developers had to carefully choose algorithms to deliver anything successfully.  Over time, resources became more abundant and tech like relational databases made routine IT application development easy.  In recent years, distributed computing has become more prevalent and forced IT developers to again pay attention to "systems" concerns.  

Another trend involves the hardware.  In earlier days, developers chose the hardware that made their software easier to write and easier to achieve performance goals, but in modern times developers must figure out how to build software that runs on provided, homogenous data center hardware.

The final trend involves how containers have evolved.  Early containers, often called "application engines" and eventually standardized via Servlets, J2EE, and .Net, focused on hosting the application logic only.  As virtual machines became viable, an entire machine from the hardware API was hosted.  Today's containers host the operating system or its processes.  This modern version of containers seems to be the best fit, the "mama bear", for IT application developers and it has seen wide adoption and enthusiasm.


## IT systems and "Systems systems"

Let's admit that it sounds silly to say "systems systems".  But we have a subdiscipline in computer science that is called "systems" ( not to be confused with the overall engineering subdiscipline called "systems engineering") and as far as I know there's no easy term for the software that the CS systems subdiscipline builds.  By "systems systems" I mean things like operating systems, device drivers, distributed systems, mail servers, and databases.  Developers of such "systems systems" traditionally spend a lot of their time working on algorithmic problems and distributed systems problems.  Systems developers tend to build long-lived software that evolves but is still recognizable decades later, often still using the same standard messages or protocols (eg TCP/IP, SMTP, SQL).

So-called "IT systems" (where the acronym IT unpacks to Information Technology, not much of a clarification in itself) aren't generally treated by academics as a subdiscipline of computer science or engineering, despite being the most common (probably overwhelmingly) kind of system built in industry.  IT applications facilitate running a commercial business and the users are (generally) not engineers or computer scientists.  Developers of IT systems traditionally spend little of their time on algorithms but a lot on messy, frequently changing business requirements.  They also do so under short deadlines.  IT developers built huge numbers of short-lived systems and a few long-lived systems whose maintainers wished they had been retired long ago.  

As a result, IT developers have created strategies for shooting at their moving target whose incoherent requirements they cannot anticipate nor refactor into consistency.  In particular, relational databases have been a critical part of the strategy and I sometimes refer to them as the Jedi lightsaber of IT development.  (NB I find that most developers don't see them that way and instead use them out of inertia -- either their project was already using one or it's simply the presumptive architecture).  Confronted with the need for multiple clients to access shared data and shifting, unpredictable requirements, relational databases provide a nearly perfect solution:  (1) safe concurrent access to shared data with little to no burden on developers, and (2) an ability to store the data today in a normalized format and expect acceptable performance when accessing that data tomorrow, or even after evolving the schema. 

In contrast, Systems developers often have the luxury of a relatively slow moving target (eg a mail server), standard formats/protocols, and flexible requirements allowing developers to homogenize or smooth over arbitrary differences.  But their quality attributes are harder, often requiring vastly better reliability, efficiency, or scale than IT systems routinely attempt.

I'm sure that this broad-stroke depiction of IT and "systems" systems is inaccurate in its details.  However, it should serve well enough to juxtapose two types of application development so I'll now turn to how IT systems have evolved over time.


## IT systems and "systems systems":  at first similar, then distinct, now becoming similar again

Here is a cartoon, oversimplified history of IT application development.  In the early days, the scarcity of computing resources meant that every IT system developer was forced to confront "systems" challenges, choose algorithms carefully, and generally little few off-the-shelf tech to make their jobs easy.  Early IT systems avoided being distributed systems as much as possible, with the earliest mainframe IT applications being basically one-tier applications.  As personal computers became dominant in the late 1980's, client-server computing became the norm for IT applications and developers had to confront distributed computing problems (which I'll consider to be a traditional "systems" problem).  Into the 1990's, issues of scale forced the server to be divided up with one machine hosting the database and one or more hosting the server-side of the application, furthering the distributed computing problem.  Then the database was too big for a single machine and was split across many machines.  Then the applications started using not just their own database but also other systems as backends and truly became a distributed system because they had to confront distributed transactions (or confront the lack of them).

This cartoon glosses over the fact that different developers confronted these changes at different times and, for example, many of them had to handle multiple backends and no transactions even in the early client-server days.  But it highlights an important trend with respect to IT vs "systems" development: For a couple of decades, IT developers could often build their applications without seriously confronting "systems" problems because the presumptive architectural patterns were so effective.  In the early days, they had to confront systems problems, then they could mostly ignore them (say 1990 - 2010), but they now have to confront them again.

To be clear, the kinds of systems problems that IT developers confront include:  RPC failures, load balancing, server stickiness and statefulness, distributed cache coherence, network partitioning, and distributed transactions (or the lack of them).  It also importantly includes the need to predict data access patterns and carefully choose data structures in advance that can execute quickly  -- something that was a non-issue when the application had a single normalized relational database.

Added to the modern challenges is the need to configure a system for testing.  Test-driven development (TDD) has been one of the best and most widely adopted Agile practices, so IT developers must figure out how to execute not just unit tests on their business logic but also integration tests on what is now a distributed system.  Patterns include re-using existing "dev" or "test" servers carefully such that different developers and different tests do not interfere (this is hard), and bringing up fresh copies of the servers for each developer or test.  The former pattern is perhaps the most common but perhaps just as common is that it fails to properly isolate developers or tests, leading to false positive failures and developers wasting time debugging ghost issues.  The latter pattern has historically been impossible (eg not enough resources on the developer's local machine to run all the backends and databases) or too expensive (virtual machines require heavy resources and take a long time to initiate, usually too long for tests when the developer is waiting but OK for batch testing).

Before discussing containers directly, it's important to look at the hardware that IT applications have run on.


## Software teams choose their hardware becomes homogenous datacenters

In the old days, you bought hardware that was suited to the task of running your software.  Thought went into choosing the right mix of processing speed, memory, storage, and database tech.  Datacenters were heterogenous.  Worse, since your hardware was not commodity, you had to order it before you had finished (or even started) writing the software.  Sometimes a higher priority project would steal your hardware order before you even received it, delaying your launch.

But then there was an inversion of primacy and the ability to scale datacenters efficiently became the most important consideration.  The hardware was homogenized.  In a reversal, software developers had to figure out how to design software that ran on the available hardware.

The pendulum has started swinging the other direction.  Datacenters now offer many types of machines (high ram, fast network, high cpu) to better match the workloads.

Current pattern languages (for code) and hardware capabilities (eg memory, cpu, io) are sufficient to handle the hardware primacy for IT and web applications.  Some large scale and compute intensive tasks must still invent their own patterns to deal with hardware primacy.


## Modern containers are the "Mama Bear" of containers

1990s container tech (application engines, eg servlets, .Net services) was too tilted towards the IT problems.  How so?  Limited access to tune performance.  Few (or single) languages.  Certainly not process-level tuning.  More of a “trust the container to load balance” etc to achieve scale, performance, etc. sometimes with horrible results compared to hand-tuned solutions.

2000’s container tech (virtual machines, eg VMWare) was too tilted towards systems problems.  Full control but ... you have to do it all yourself.  Still very manual (until the late 2000’s as scripting started to arrive).  Convenience of running a VM, relocating it, sharing images, but per-machine efficiency not great.

2010’s container tech (lightweight containers, eg Docker, Kubernetes) seems like the right fit between IT and Systems problems.

As described above, current IT systems are in some ways confronting systems problems but aren’t ready (and arguably shouldn’t be distracted) with all the knobs and details of pure systems problems and their container tech.  Scripting and out-of-the-box usability is much better, as is per-machine efficiency.  Developers can spend less % of their attention on the deployment aspects compared to earlier container tech while getting better results.
