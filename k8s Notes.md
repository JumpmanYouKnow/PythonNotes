---
title: "Kubernetes Notes"
date: 2019-04-19
---
Table of Contents:
* [Basic Terms]()
* [Run a service]()
* [Expose a service]() 
* [Secret, ConfigMap]() 
* [Volume and PersistentVolume ]() 
* [Autoscaling]()
* [Helm]()

###  Basic Terms
	cluster, context, namespace, node, pods.
1. **cluster**: physical cluster of physical machine.
2. **context**: a group of access parameters,  a cluster, a namespace, a user.
3. **namespace**: virtual cluster, use to separate resources across different environments like prod, dev, test.
4. **node**: a virtual/physical machine
5. **pod**: a set of containers to orchestrate, minimal object to scale
6. **container**: docker container runs in pod
7. **Job**: usualTasks that run only once
### 

- Deployment: deploy a service
- DaemonSet: 
- ReplicaSet

- ReplicasSet: Like name, replicas, 
- DaemonSet: A job that runs on 
### manifests/objects
	Pod,Service,Volumes,HorizontalPodsAutoscaler(HPA)
	ususally defined by .yaml or .json file


### Access pod(s) by service
1. Create a ```Kind:Service ``` yaml, and define which pods your service is using (by using label)

### Expose a service
There are 3 types of manifests to expose a service
1. **NodePort**:  Assign the service to a port, access the service by port number. Ex:```<NodeIP>:<PortNumber>```, PortNumber is fixed, NodeIP could be any node that the service is running on. pods traffic is balanced in the same node, but not balanced in the different nodes . This is not good for production, but good for local testing by using kube-proxy.
3. **LoadBalancer** Similar to NodePort, but expose the all ```<NodeIP>:<PortNumber>```to a external load balancer. Node traffic is balanced.
4. **Ingress** Recommended way for production. 
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4OTI4MTY3NjldfQ==
-->