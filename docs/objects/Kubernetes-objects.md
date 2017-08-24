**Kubernetes Objects** are persistent entities in the Kubernetes system. Kubernetes uses these entities to represent the state of your cluster.
* What containerized applications are running (and on which nodes)
* The resources available to those applications
* The policies around how those applications behave, such as restart policies, upgrades, and fault-tolerance

A Kubernetes object is a “record of intent”–once you create the object, the Kubernetes system **will constantly work to ensure** that object exists.

Object Spec and Status.
* Every Kubernetes object includes two nested object fields that govern the object’s configuration.
  * The **spec**, which you must provide, describes your desired state for the object
  * The **status** describes the actual state of the object
  
Names:
* All objects in the Kubernetes REST API are unambiguously identified by a Name and a UID.
* For non-unique user-provided attributes, Kubernetes provides labels and annotations.

Namespaces:
* Kubernetes supports multiple virtual clusters backed by the same physical cluster.

```Namespaces are intended for use in environments with many users spread across multiple teams, or projects. For clusters with a few to tens of users, you should not need to create or think about namespaces at all. Start using namespaces when you need the features they provide.```
* Namespaces provide a scope for names. Names of resources need to be unique within a namespace, but not across namespaces.
* Namespaces are a way to divide cluster resources between multiple uses (via resource quota).
* In future versions of Kubernetes, objects in the same namespace will have the same access control policies by default.
* It is not necessary to use multiple namespaces just to separate slightly different resources, such as different versions of the same software: use labels to distinguish resources within the same namespace.

**Not All Objects are in a Namespace**
* Most Kubernetes resources (e.g. pods, services, replication controllers, and others) are in some namespaces. 
* However namespace resources are not themselves in a namespace. 
* And low-level resources, such as nodes and persistentVolumes, are not in any namespace. 
* Events are an exception: they may or may not have a namespace, depending on the object the event is about.

Labels and Selectors:
* Labels are key/value pairs that are attached to objects, such as pods.
* Labels can be used to organize and to select subsets of objects.

Annotations:
* You can use Kubernetes annotations to attach arbitrary non-identifying metadata to objects. 