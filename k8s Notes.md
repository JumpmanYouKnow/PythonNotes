---
title: "Kubernetes Notes"
date: 2019-12-18
---
Table of Contents:
* [Basic Terms](#Basic-Terms)
* [Manifests](#Manifests)
* [Expose a service](#Expose a service) 
* [Helm](#Helm)

# Basic Terms
	cluster, context, namespace, node, pods.
1. **cluster**: physical cluster of physical machine.
2. **context**: a group of access parameters,  a cluster, a namespace, a user.
3. **namespace**: virtual cluster, use to separate resources across different environments like prod, dev, test.
4. **node**: a virtual/physical machine
5. **pod**: a set of containers to orchestrate, minimal object to scale
6. **container**: docker container runs in pod
7. **Job**: a wrapper to pod, usually runs a pod that carrying tasks that run only once, like db migration.
8. **Service**: a wrapper to pod, one or more pods to perform a service.
9. **Volumes**: file storage system, lives with node. Can define externel volumes on cloud providers, lives with cloud providers.
10.**Label**: To classify different kind of pods. 
 

# Manifests
manifests usually defined by .yaml or .json file, to manage resources.


	- Deployment: deploy pods based on spec
	- ReplicaSet: deploy pods as replica 
	- DaemonSet:  deploy pods based on spec, ensure each node get one replica.
	- HorizontalPodsAutoscaler(HPA): Autoscaler for pods, make sure the resources usage keeps at same level.(50% CPU/Memory Usage)
	- Volume Claim Chain: To better manage a externel volume, to use a volume, must first claim it.
	- Network Policy: Define a network policy to a set of pods(by label) like which set of pods(by label) or users(by namespace) can access.


### Expose, Access pod(s) by service
1. Create a ```Kind:Service ``` yaml, and define which pods your service is using (by using label)

There are 3 types of manifests to expose a service

1. **NodePort**:  Assign the service to a port, access the service by port number. Ex:```<NodeIP>:<PortNumber>```, PortNumber is fixed, NodeIP could be any node that the service is running on. pods traffic is balanced in the same node, but not balanced in the different nodes . This is not good for production, but good for local testing by using kube-proxy.

2. **LoadBalancer** Similar to NodePort, but expose the all ```<NodeIP>:<PortNumber>```to a external load balancer. Node traffic is balanced.

3. **Ingress** Recommended way for production. 
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIzNjMzMTY4Nyw5ODQzNDIzNTMsMjAyND
kzOTE2NSwxODEyMTM4MDc4LDE3MzU0MjU5ODksLTEzMzM2MTM0
OCwtODg0MzMyNjQxLDEyNzAxNDE2MzEsMzg4Nzc2MjgwLDY0Mj
g3OTQ2XX0=
-->