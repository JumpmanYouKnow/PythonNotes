---
title: "Kubernetes Notes"
date: 2019-12-18
---
<br>
Kubernetes cheatsheet and notes, wrote while learning and working on k8s related projects. <br>

## Table of Contents:
* [Basic Terms](#Basic-Terms)
*  [Tools](#Tools)
* [Manifests](#Manifests)
* [Expose A Service](#Expose-A-Service)
* [Helm](#Helm)

# Basic Terms
	some basic termnologies used by kubernetes
1. **cluster**: physical cluster of physical machine.
2. **context**: a group of access parameters,  a cluster, a namespace, a user.
3. **namespace**: virtual cluster, use to separate resources across different environments like prod, dev, test.
4. **node**: a virtual/physical machine
5. **pod**: a set of containers to orchestrate, minimal object to scale
6. **container**: docker container runs in pod
7. **chart**: a collect of files that describes your pod orchestration, that can be used to deploy a set of pods.
8. **Job**: a wrapper to pod, usually runs a pod that carrying tasks that run only once, like db migration.
9. **Service**: a wrapper to pod, one or more pods to perform a service.
10. **Volumes**: file storage system, lives with node. Can define external volumes on cloud providers, lives with cloud providers.
11. **Label**: to classify different kind of pods. 
 
# Tools
kubectl, kubeadmin, minikube, helm
1. **kubectl**: user tool to interact with the cluster
2. **kubeadm**: admin tool to setup a cluster
3. **minikube**: setup & run a single node cluster locally for testing and dev purpose.
5. **helm**:  charts manager

# Manifests

manifests usually defined by .yaml or .json file, to manage (describe) resources.

	- Deployment: deploy pods based on spec
	- ReplicaSet: deploy pods as replica 
	- DaemonSet:  deploy pods based on spec, ensure each node get one replica.
	- HorizontalPodsAutoscaler(HPA): Autoscaler for pods, make sure the resources usage keeps at same level.(50% CPU/Memory Usage)
	- Volume Claim Chain: To better manage a externel volume, to use a volume, must first claim it.
	- Network Policy: Define a network policy to a set of pods(by label) like which set of pods(by label) or users(by namespace) can access.


# Expose A Service


1. Create a `Kind:Service` yaml, and define which pods your service is using (by using label)

There are 3 types of manifests to expose a service

1. **NodePort**:  Assign the service to a port, access the service by port number. Ex:`<NodeIP>:<PortNumber>`, PortNumber is fixed, NodeIP could be any node that the service is running on. pods traffic is balanced in the same node, but not balanced in the different nodes . This is not good for production, but good for local testing by using kube-proxy.

2. **LoadBalancer** Similar to NodePort, but expose the all `<NodeIP>:<PortNumber>=`to a external load balancer. Node traffic is balanced.

3. **Ingress** Recommended way for production. 

# Helm
Helm is like a manager of `charts`, you can use helm to pull, push, deploy `charts`.


- get  values.yaml of a chart 
``

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNjgyMDEyNDQsLTE4OTcxMjAzNzAsMT
I1NTY2MjAzNyw0NjkyMzQ1MDYsLTcwNTE1Njc0MSwtNDExODU1
NzA0LDk4NDM0MjM1MywyMDI0OTM5MTY1LDE4MTIxMzgwNzgsMT
czNTQyNTk4OSwtMTMzMzYxMzQ4LC04ODQzMzI2NDEsMTI3MDE0
MTYzMSwzODg3NzYyODAsNjQyODc5NDZdfQ==
-->