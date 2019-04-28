---
title: "Kubernetes CheatSheet"
date: 2019-04-19
---

###  list of terms
	cluster, context, namespace, node, pods.
1. **cluster**: physical cluster of physical machine.
2. **context**: a group of access parameters,  a cluster, a namespace, a user.
3. **namespace**: virtual cluster, use to separate resources across different environments like prod, dev, test.
4. **node**: a virtual/physical machine
5. **pod**: a set of containers to orchestrate, minimal object to scale
6. **container**: docker container runs in pod

### manifests/objects
	depolyment, replicas, Persistent Volumes,
	ususally defined by .yaml or .json file

### Expose a servcie
3 type of manifests to expose a service
1. **NodePort**:  Assign the service to a port, access the service by port number. Ex:```<NodeIP>:<PortNumber>```, PortNumber is fixed, NodeIP could be anynode that the servcie is running on. pods traffic is balanced in the same node, but not balanced in the different nodes . This is not good for production, but good for local testing by using kube-proxy.
3. **LoadBalancer** Similar to NodePort, but expose the all ```<NodeIP>:<PortNumber>```to a external load balancer. Traffic is balanced 
4. **Ingress**
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNDU4NjEwNTIsMTA5NjYzNjA1OSwyNz
c0NzkzNTcsLTEwNTY0NDI3Miw3ODkxNzM0OTMsMTM2MDU3Mjc2
MCwxNjY1MTU0NzgyLC0yMjExMjkyNTQsLTIyNTA0NjQzOSw4Mj
c4NTM4NTZdfQ==
-->