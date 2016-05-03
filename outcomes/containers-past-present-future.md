# Past, present, future of containers

## Past:
 - Java ecosystem (Tomcat, WAR, Jar)
 - Openshift [gears](http://thenewstack.io/red-hat-openshift-part-1-from-gears-to-docker/)
 - Tuxedo (isolated services, shared data spaces)
    * running things as daemons, "If this crashes, please restart"
 - OSGi containers
 - Erlang - [process isolation](http://cacm.acm.org/magazines/2010/9/98014-erlang/fulltext)
 - Vagrant + VirtualBox (an evolutionary/transitionary technology - leading to Docker)
   - [`vagrantfile`](https://www.vagrantup.com/docs/vagrantfile/) -> [`dockerfile`](https://docs.docker.com/engine/reference/builder/)
   - [Vagrant Boxes](https://www.vagrantup.com/docs/boxes.html) -> [Docker Hub](https://docs.docker.com/docker-hub/repos/)

### Good

* conceptual separation of concerns
* rigid thinking - there is a right way
* configuration as code...

### Bad

* actual isolation was poor 
* lousy management interfaces
* difficult deployment
* rigid thinking
* producing the artifact was extremely manual
* heavy, slow (especially VirtualBox)

## Present:
 - Java ecosystem - lighter weight, embedded services (e.g. embedded Jetty versus deploying on Tomcat/Websphere)
 - Docker
 - Karaf
 - Fabric8
 - Orchestration management of Docker
 - CoreOS
 - Deployment is an "interesting problem" - costly[1](https://dougseven.com/2014/04/17/knightmare-a-devops-cautionary-tale/),

Present tools are based on homogeneous environments (Linux)
 - they are also API-driven

### Good

* even more opinionated
* lightweight, do one thing well
* pattern language, deployment pipelines
* tool support

### Bad

* community diversity is not there yet
* we don't fully understand or explain implications of use/patterns
* security - as bad as it was before, but now everyone is using the same base components
* container as script kiddie
* single device OS is still visible and relevant

## Future:
 - open containers
 - thrid party integration with container ecosystems
 - common language, vocabulary, concepts for deployment
 - component-driven development
 - greater responsibility on developer
   - more power
   - more complexity, more to manage
 - containers disappear into the infrastructure

"The future is already here. It's just not evenly distributed."

