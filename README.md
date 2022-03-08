# kubernets_learning

# PODS and multi containers

https://www.mirantis.com/blog/multi-container-pods-and-container-communication-in-kubernetes/

- a Pod can contain more than one container, usually because these containers are relatively tightly coupled. 
- How tightly coupled?  
  - Well, think of it this way: the containers in a pod represent processes that would have run on the same server in a pre-container world.

> Conclusion: Multiple containers in a pod act like multiple servers on a host. Eg: django server at 8000, reactjs at 3000. So there cannot be port conflict

> a Pod acts like a single server. For example, each container can access the other containers in the pod as different ports on localhost.

# Why does Kubernetes use a Pod as the smallest deployable unit, and not a single container?

What’s more, **Kubernetes needs additional information for container management**, such as a **restart policy**, which defines what to do with a container when it terminates, or a **liveness probe**, which defines an action to detect if a process in a container is still alive from the application’s perspective, such as a web server responding to HTTP requests.

Instead of overloading the existing “thing” with additional properties, **Kubernetes architects have decided to use a new entity, the Pod**, that logically contains (wraps) one or more containers that should be managed as a single entity.

![](https://i.imgur.com/nE9YkFx.png)

