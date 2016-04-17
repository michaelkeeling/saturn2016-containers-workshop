# Using containers to keep costs down while maintaining security

Harald Wesenberg

SATURN 2016 Containers Workshop Position Paper


When working for a large multinational oil company, there are always many competing interests
at play. As developers we want to have as much freedom as possible to install, test, and change
our environments including production, while on the other hand the infrastructure operations
people want to limit the number of different configurations in productions, as well as
restricting developer access rights to increase security and limit the damaging possibilities
of rogue or incompetent developers.

Containers offer a middle road between these competing interests, and we have been successfully
deploying software in containers for some time. Based on experiences from our use of containers,
we see that this approach offers several benefits as outlined in this position paper.

## Reduced access requirements for developers in production

The background checks required for administrative privileges in production servers are 
comprehensive, and thus also expensive. We try to keep the number of people with administrative 
privileges as low as possible. This is mandated by our corporate regulations, but it is of
course also sensible security practice (although our developers do not always seem to understand 
this). Our practice limits the amount of damage that a rogue developer or development team can do, 
and also limits the amount of damage that incompetent or inattentive developers can do. 

Through the use of containers, we limit the need for developers to have substantial access rights
in our production environment. They can keep administrative privileges on their own workstations 
and in low risk test and integration environments, where they are also able to configure containers 
and set up applications properly. Once the container is setup and the application installed, it can 
progress through the test, acceptance and production environments all without the developers needing 
extended access rights to the servers.

## Reduced requirements to staging environments

To reduce the risk of introducing severe errors into our production environments, we have always run
multiple staging environments. The closer we get to the production environment, the more the staging
environment is set up to mimic the production environment both in terms of data and configurations. 
In a large corporation with thousands of applications, we have always had a large number of staging
pipelines for these applications running with resulting license costs, storage costs and personnel 
costs. Depending on the deployment properties of a particular application, parts of the staging pipeline 
may be dormant 90% of the time, only being used whenever deployments are passing through.

We are moving towards continuous deployment for many of our applications (especially internally developed
ones), but we see that we will maintain a large portfolio of semi-automated, infrequently deployed 
applications for some years to come. If these applications can be containerized, we would expect this
to offer some cost saving possibilities:

* **Reduced need to mimic production server configurations**: By abstracting away the server/infrastructure 
  layer, we also reduce the need to accurate mimic these environments in our staging environment pipelines. 
  Ideally we would be able to run a heterogeneous staging environment with low cost server infrastructures
  much further towards to our production environments than we do today. As long as the container hosting 
  mimics production properly, we can use low cost OSes and low end server configurations.
* **Reduced need for separate staging environments**: Today, applications are deployed at irregular intervals
   depending on release cycles, vendor practices and more. Whenever there are no deployments moving through 
   the staging environments, the environments are idle. This may be as much as 90% of the time, however, 
   it would still be prohibitively costly to demobilize and mobilize these environments each time they are 
   needed. By containerizing the applications, we can utilize a smaller number of staging environment servers 
   and infrastructure that are more efficiently utilized.


## Reduced coordination needs reduce operational cost

Back in 2014, Jørn Ølmheim and I gave a talk titled 
[What happens if you break all the rules](https://www.youtube.com/watch?v=_Wa8Ekx3-aA). 
One of the key messages in this presentation is that coordination and lack of competence are the 
most important cost drivers for an IT operations organization. As we move towards better DevOps practices, 
we see that some of the previous coordination needs disappear. However, we still see a need for DevOps 
teams and server/infrastructure teams to interact during the final stages of the deployment process especially 
for those applications where deployment is not fully automated.

Containerizing applications takes away a lot of the coordination needs. By allowing the DevOps teams to 
deploy directly into the containers, we enable the DevOps teams to perform the deployment without interaction 
with the server/infrastructure teams. This limits the amount of application specific competence required for 
the infrastructure teams (especially important when there are thousands of applications), while at the same 
also limiting the production specific infrastructure competence required for the DevOps team. 
