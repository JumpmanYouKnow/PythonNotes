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
1. **NodePort**:  Access service by a port number,
2. **LoadBalancer**
3. **Ingress**
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDE2MDY5ODgxLDI3NzQ3OTM1NywtMTA1Nj
Q0MjcyLDc4OTE3MzQ5MywxMzYwNTcyNzYwLDE2NjUxNTQ3ODIs
LTIyMTEyOTI1NCwtMjI1MDQ2NDM5LDgyNzg1Mzg1Nl19
-->