SATURN 2016 Containers Workshop Position Paper

[Michael Keeling](http://www.neverletdown.net/) | [@michaelkeeling](https://twitter.com/michaelkeeling)

# Our Understanding of the Allocation Style is Underdeveloped

I fined allocation patterns fascinating.  Allocation views map the 
abstract software components of an architecture to things that exist
in the real world. Some of the common patterns include _deployment_, 
_work assignment_, and _installation_. And that's it basically it.

[Documenting Software Architecture: Views and Beyond](http://amzn.to/25pJuLf)
spends about 140 pages of the book describing Module and Component and Connector
architectural styles and views and only 20 pages for Allocation.  **Only 20 pages
of reference material are given to the views in the architecture that show how a
software system manifests in the real world.**

The most recent edition of _Views and Beyond_ was published in 2010 and 
pre-dates the popular rise of containers by three years with Docker, CoreOS, 
and lmctfy all released in 2013.  Yes, cgroups existed in Linux before this 
but it largely didn't matter until the tools, ecosystem, and community of Docker 
made containers accessible to the mob of average developers.

Meanwhile, rigorous notations and patterns -- critical design tools for 
communication, reasoning, risk reduction, planning, and decision making
-- have remained woefully out of date.  Container based allocation patterns
require a level nuance that the average developer and architect don't fully
understand.  This is completely normal.  All design trends go through an 
informal growth stage where heuristics and rules of thumb from the foundation
of knowledge.

The use of containers has grown so fast and taken hold so quickly that we
need to move beyond informal design heuristics soon or suffer consequences.
Some teams already are suffering.


## My Hopes for this Workshop

I'd love to see a new architectural style defined for container based architecture,
one that goes beyond just using the word container.  A nice-to-have goal is
defining a few patterns that use the style.

If container-based allocation views can be described and analyzed using existing
architectural styles, it would be great to create a few examples demonstrating
what this looks like.

Regardless, it seems that the lowly allocation view needs some love.  There are
now potentially multiple granularities of abstraction and refined views required
to describe how components are allocated to both containers and physical hardware.

Some questions that need to be answered to create such a style include the following.

* What are the key quality attribute concerns addressed by container-based allocations?
* What are the essential elements and relations in a container allocation style?
* What notations work best for effectively communicating and reasoning about containers?
* How is the "containers style" related to other allocation, module, and component and 
  connector styles?

**Bottom line**: If you could summarize everything a person needs to know about containers
on a single page so they can effectively think and communicate, what would go on that 
page?
