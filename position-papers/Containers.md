##Overview
Containers have been talked about in the same way as the second coming for the last few years by a large portion of the tech world; however, the impact on the architecture of systems has been skimmed over more. As a conference organizer, I’ve read many Docker proposal but all are in the view point of the developer or tester.

The main quality attributes enabled by containers are reliability, testability, modularity, and modifiability.  A system can use docker or other containers to test unusual configurations for each part of the architecture. This faster testing allows for more to be done and a system to be in theory more reliable. 


##Modularity and Testability 

Architecting a system with the addition of containers in mind makes the idea of several modules even more practical. Since each piece can be tested more in depth, each section is more reliable in its own right. Extra abstraction has already been added so it resembles the abstraction layer-though very different-that is used for making modules. 


##Security
Are containers an improvement on security of systems? It’s debatable. Most articles online will state that containers are less secure than VMs, which is true, but what about in comparison to a lack of virtualization in general? A good use for containers to make a system more secure is the ability to spit up a new instance of a user application. Then if any user choses to malicious and mess with the system, it can just be easily blown away rather than potentially impacting anything long term. Since a container share the same kernel as all other containers in this portion, a black hat getting root access would be able to completely bring down the entire cluster, but if a user is able to get root permission, there are bigger security issues at hand. The other side of this argument is that adding an extra layer of abstraction makes the system make complicated. Complication can lead to cracks and security lacks.


##Complicated Systems
It seems like Docker is magic sometimes. Are there any weird situations that can arise from using multithreaded systems or streams in conjunction with clustering of containers?
