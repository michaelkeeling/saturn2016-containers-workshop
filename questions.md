# Some Questions for Thought

Write once run anywhere.  Over the years many technologies and design paradigms have made this promise.  Virtual containers such as Docker and CoreOS may finally be the technology that truly delivers on the promise.  But with all new powers developers must be prepared for a new set of responsibilities.  Containers may bring portability but with it comes new abstractions.  Scalability might be achievable but only when certain patterns are followed.  Like all the magic that came before it, an improper understanding of the abstractions underneath brings calamity.

In this workshop we plan to explore the architectural implications of containerization. Based on what we learn, we'll create posters at the end of the day to summarize our findings so we can share what we've learned with the SATURN community. Some questions and topics we will consider during the workshop include the items listed on this page.


## Understanding new Abstractions

* What is a container?  Is there a practical definition?  Is this definition sufficient for architectural reasoning or is a different definition required?
* What are the key abstractions to understand containerization?
* Are there design concepts or ideas that are common across vendor specific implementations?
* How are containers different than frameworks?  When should each be used?

## Reasoning about the System

* How do containers change the ways we should think about system design? 
* What quality attributes matter in a containerized world?  What properties are promoted?  Inhibited?
* What new tensions among quality attributes are created that may not have existed prior to a containerized world?
* What views do containers help with?
* What new questions should we ask about allocation and deployment? 
* Are existing architectural styles sufficient as defined?
* What are the benefits of containers?  Who gets those benefits?

## Implementation Concerns

* What new risks and trade-offs are introduced by adopting containers?
* What development practices and team organization are assumed when using container-based allocation patterns?
* What is the connection with DevOps?  Ho much DevOps maturity is required? Suggested? Optional?
* What is the connection to cloud allocation and deployment patterns?
