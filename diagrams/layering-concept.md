# Layered Diagramming

Kubernetes provides an Abstraction over the Infrastructure, to put it in perspective it gives us only one endpoint and it suffices to **manage the infrastructure** and **orchestrate the application**, and that is made possible by a small set of **resources**. 

This absctraction hides an enormous amount of detail and that's why diagramming is so difficult. How to know if we are making the diagram difficult to understand with too much information, should you display this information, if not where should it go.

These questions are resolved with the **Layered diagramming** approach, where each layer serves to answers one specific question.

## Layers
For the graphical presentation please see the [pdf](./Layers.pdf)

### Infrastructure
* Whom does this layer serve?

**Infrastructure Administrators** who need to know with regards to system setup and networking where which components are located and their relationship
* What information is expected on this layer
    * Master VMs
    * Node VMs
    * LoadBalancer


### Application
* Whom does this layer serve

**Developers** who need to know how the components of the application (i.e. microservices) interact with each other.
* What information is expected on this layer
    * Services
    * Deployments
    * Network policies

### Resource (Suggestion 1)

* Whom does this layer serve
DevOps who need to know how everything is configured.

* What information is expected on this layer
    * Kubernetes resources that are related to one specific Microservice.

* What does this suggestion lack:

This approach leaves out Roles, ClusterRoles, RoleBindings etc. These are Kubernetes resources, as such their place would be in the Resource Layer.
(Should a diagram deal with these resources?)

### Resource (Suggestion 2)
* Whom does this layer serve:

    * **Kubernetes Administrators** for engineering and troubleshooting setups
    * **Application Developers** for configuration of services, i.e. on what ports are containers run, how is a container configured, on what configurations it is dependent.

* What information is expected on this layer:
    * An example of the suggestion [Link](https://blog.openshift.com/kdl-notation-kubernetes-app-deploy/)


### Resource (Suggestion 3)
* Whom does this layer serve:

    * App developers who are managing app resources; i.e.:
        * Scaling resources, 
        * Updating resources, etc. 
        (These tasks may skew more towards what DevOps might do)

        * What information is expected on this layer
        Resource config (specs; capacity)
        Resource current state (usage)
        Any resource controllers perhaps