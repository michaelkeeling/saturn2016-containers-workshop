SATURN 2016 Containers Workshop Position Paper

[Eoin Woods](http://eoinwoods.info) | [@eoinwoodz](https://twitter.com/eoinwoodz)
16th April 2016

# Containers as Architectural Elements - better zip files or a new architectural style?


## Containers in Context

Containers are a lightweight virtualisation mechanism that allow software elements to packaged in such a way that they run as isolated lightweight virtual machines without the overhead of the virtual machine and operating system being duplicated within each container, so making them much more efficient than VMs.  The best known containerisation technology is Docker, to the point where it has become the "Hoover" product in its field, and people talking about "containers" are often actually talking about Docker and when people say "Docker" they often mean "containers".

Docker was originally created by Solomon Hykes in about 2012, as an internal project within his company, dotCloud, an early PaaS provider.  It was created with the aim of creating an efficient mechanism to isolate hosted applications from each other, without all of the overhead of creating a VM for each.  Since then, the project has taken on a life of its own to the point where it was spun out of dotCloud (which subsequently closed down), attracted $150m of venture capital funding, and strategic partnerships with industry giants like IBM and Microsoft. 

Today, containers are the darlings of the industry, with nearly every software company talking about how they relate to their offerings, cloud providers integrating them as first class infrastructure components and the DevOps movement claiming them as their own, using technologies like Docker to ease the pain of the path to production and allow better collaboration between development and operations people.

Look closely though and it quickly becomes clear that different communities are using containers for different reasons and at this point they become very interesting from an architectural perspective.

## Containers as an Architectural Element

In the work we've done with containers at Endava and observing the wider software engineering community in London and beyond, a number of common motivations for using containers emerge:

* Using containers as a neat packaging mechanism to allow dependencies to be managed, particularly when moving into production environments.
* Using containers as a "DevOps tool" that provides an easy collaboration point for both development and operations staff to work on.
* Using containers as an efficient way to maintain isolation of runtime environments without the overhead of virtual machines, and greating improving ease of use (e.g. much easier creation, lighting fast stop and start, etc).
* Using containers as a support technology specifically to enable so called micro-service based architectures, providing a useful and lightweight mechanism for packaging, deploying, managing and isolating micro-services.

Each of these uses is valid and they are not exclusive, containers can often be chosen for a blend of these roles.  However they do have different levels of architectural impact, from a fairly minor impact on the deployment tool chain (when used as a handy packaging mechanism) to a profound impact (when used as the enabler of the microservices architectural style).

At this stage I think I have more questions than answers when it comes to the architectural impact of containers, but some observations I have about them would be as follows:

1. Container technologies like Docker are often driven from the development community in an organisation and the operational teams often don't know much about them.  They're generally presented as a wonder solution for deployment but the operations teams don't know how to work with them, validate them and in particular operate them reliably.
1. That said, as a packaging technology we've found Docker in particular to be very valuable for the applications where we've used it.  One of its main benefits has been the way that it eases the development to operations interaction, with (simplistically) the stuff in the container being primarily a "dev" problem and the stuff outside the container being primarily an "ops" problem, but the overall entity being a shared artefact.
1. We have observed some of the same concerns around third party container dependencies (e.g. from DockerHub) as we've had with previous library dependency management tools like Maven and NuGet, where there's a lot of implicit trust in the dependencies being downloaded.  We're very much relying on the wisdom of the crowd to spot malicious or unintentional problems in third party containers (as we do today for software on Maven Central, for example).  This is a significant architectural concern, given the architect's accountability for overall technical integrity.
1. Another system quality concern is the security of containers, given their reliance on the security of the underlying Linux operating system, with its all powerful "root" user.  This is an area that is evolving quickly and needs to be well understood in the context of the security requirements of the system being developed.
1. From a development perspective, containers seem to work really well as a lightweight isolation mechanism.  The ability to compose them easily, share them, their speed and relative simplicity are all compelling from a development point of view.  The operational point of view is still emerging.  Outside very early adopters and the most sophisticated firms (like Google and Facebook) there is relatively little operational experience of using containers for mainstream systems.  Given the architect's responsibility for ensuring effective operation as well as design of the system, this is a significant architectural concern at present.
1. At Endava we work in a very multi-platform world, in particular we have a lot of client demand and interest in Microsoft Windows as a data centre platform.  This sometimes causes quite a lot of confusion given the preliminary support for containers on Windows.  It will be some time before most Windows customers are running Windows Server 2016!  (The version promising native container support).
1. Finally, we're starting to build systems using microservices and containers are a nice solution to a number of architectural concerns around standardisation, dependency management, deployment, isolation and operational control.  In particular, containers allow PaaS platforms to offer powerful facilities in a standard way that is familiar to developers already and are a good match for the demands of microservice based systems.

## Conclusions

So to summarise a position on the use of container technology from the architect's perspective, I see the following themes emerging:

* Containers are here to stay given their usefulness and industry backing.  Architects need to understand them and know when and where to apply them as many people will want to do so.
* Like a lot of "DevOps" technologies, containers appear to be emerging with support primarily from the development rather than the operational communities, and we're only starting to see the emergence of the technology and knowledge required to support operation of large container based systems.
* Containers can be a really valuable collaboration point between development and operations people and the architect can capitalise on this to achieve the sort of smooth path to production that we're all aiming for.
* Containers are largely a Linux phenomina at this stage and it looks as if that's going to be the case for some time.  Architects need to consider how to react to this.  Is it an opportunity to push to that platform?  Or an obstacle for the moment?
* Today "containers" tends to mean Docker and while there are alternatives and emerging standards, the architect needs to be aware of the single community dependency that is part of adoption.
* There are potential threats to system integrity from the use of untrusted third party components.  Docker Hub's "official repositories" are a useful step in the right direction but are a drop in the ocean when it comes to the amount of software that will be implicitly referenced from container configurations.  Architects need to understand this threat and have a strategy for mitigating it.  Particularly given the complexity (and trusted nature) of much of the software that is packaged as container images.
* The applicability of containerisation beyond microservices is still being understood in practice and architects need to be wary of being dragged to containers though microservices or microservices though containers.  The two are at quite different levels of abstraction!

In summary, containers will probably become as much a part of our future architectural landscape as virtual machines and code repositories are today.  Their architectural impact is actually likely to be higher than either of those examples and so now is the time for the architecture community to be engaging with this technology and bringing our skills of abstraction, analysis and contextualisation to help mature it.




