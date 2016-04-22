#Containers: For Better or Worse
####Jenny Manning

##Overview
In the last few years, containers have been regarded the same way as the second coming by a large portion of the tech world; however, their impact on the architecture has been skimmed over more. As a conference organizer, I’ve read many Docker proposal but all are in the view point of the developer or tester. Why is it this? How can containers help when designing systems and are they actually helpful?

Countless quality attributes are affected by the introduction of containers. The most interesting ones are reliability, testability, modularity, modifiability, and security.

##Modularity and Testability 

Architecting a system with containers in mind makes isolation into modules practical and almost obvious. Since each piece can be tested more in depth, each section is more reliable in its own right. Additional abstractions have already been added so it resembles the abstraction layer-though very different-that is used for making modules. Do containers help make a system more modular? Is there a positive effect of using containers for modules rather than a framework? It's easy to think that if modules fit well for containers, then containers make sense for modules. Are either of these views accurate?

##Reliability and Modifiability
A system can use docker or other containers to test unusual configurations for each part of the architecture. This faster testing enables in theory more tests and a more reliable system. Additionally, the ability to quickly test new environments and scenarios makes a system more flexible and modifiable. Cases that were previously never going to occur can now be run for even a small code to check for consistency. Is anyone testing more with this extra time saved by containers? There are always going to be infinite test cases available. Does the addition of containers result in more testing and reliable system in practice?

##Security
Are containers an improvement on security of systems? It’s debatable. Most articles online will state that containers are less secure than VMs- which is true. What about in comparison to a lack of virtualization in general? 
In a system that has a user facing application, containers can be useful for security. It can be made more secure by containers through their ability to easily spit up a new instance of a user application. If a user choses to be malicious and mess with the system, then it can easily be blown away rather than potentially impacting anything long term. Since a container shares the same kernel as all others on that machine, a black hat getting root access would be able to completely bring down the entire cluster. However, if a user is able to get root permission, then there are bigger security issues at hand. The other side of this argument is that adding an extra layer of abstraction makes the system make complicated. Complication can lead to cracks and security leaks. When does adding abstraction help with security rather than become too much? Where do containers fall in this spectrum?


##Complicated Systems
It seems like Docker is magic sometimes. Are there any weird situations that can arise from using multithreaded systems or streams in conjunction with clustering of containers?
