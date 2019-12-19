---
title: "Kubernetes Notes"
date: 2019-12-18
---
<br>
Kubernetes cheatsheet and notes, wrote while learning and working on k8s related projects. <br>

## Table of Contents:
* [Basic Terms](#Basic-Terms)
* [Manifests](#Manifests)
* [Expose A Service](#Expose-A-Service)
*   [Tools](#Tools)
	* [Kubectl](#Kubectl)
	 * [Helm](#Helm)
	 * [Kubeadmin](#)


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
 

# Manifests

manifests usually defined by .yaml or .json file, to manage (describe) resources.

	- Deployment: deploy pods based on spec
	- ReplicaSet: deploy pods as replica 
	- DaemonSet:  deploy pods based on spec, ensure each node get one replica.
	- HorizontalPodsAutoscaler(HPA): Autoscaler for pods, make sure the resources usage keeps at same level.(50% CPU/Memory Usage)
	- Volume Claim Chain: To better manage a externel volume, to use a volume, must first claim it.
	- Network Policy: Define a network policy to a set of pods(by label) like which set of pods(by label) or users(by namespace) can access.
	- Secret: some secret you don't want others to know: ssh key, username/password
	- Ingress:


# Expose A Service


1. Create a `Kind:Service` yaml, and define which pods your service is using (by using label)

There are 3 types of manifests to expose a service

1. **NodePort:**  Assign the service to a port, access the service by port number. Ex:`<NodeIP>:<PortNumber>`, PortNumber is fixed, NodeIP could be any node that the service is running on. pods traffic is balanced in the same node, but not balanced in the different nodes . This is not good for production, but good for local testing by using kube-proxy.

2. **LoadBalancer:** Similar to NodePort, but expose the all `<NodeIP>:<PortNumber>=`to a external load balancer. Node traffic is balanced.

3. **Ingress:** Recommended way for production. 

# Tools
kubectl, kubeadmin, minikube, helm
1. ## kubectl: 
	**kubectl** is a user tool to interact with the cluster
	1. **get info about the cluster (pod, service, deployment, replicaset, statefulset etc):**<br>
	everything: `kubectl get all`
	pods:  	`kubectl get pods`
	nodes:`kubectl get nodes`
	**Note:** can be filtered by namespace or label. 
	
	2. **get logs for a pod:** <br>
	usage: `kubectl logs -h`
	
	3. **forward a request from a port:** <br>
	usage: `kubectl port-forward -h`
	
2. ## Helm
   **Helm** is like a manager of `charts`, you can use helm to pull, push, deploy a chart and modify (upgrade) a depolyment.

   1. **pull  repo from [remote chart repository](https://helm.sh/docs/topics/chart_repository/) to local:**<br>
 `helm repo add [repoName] [RepoUrl]`
`helm update`

   2. **deploy (install)  chart from local repo:**<br>
`helm install [repoName]/[chartName] [releaseName]`
	**[releaseName]** can be auto-generated using `--generate-name` 
	4. **upgrade:**<br>
 -- get  values.yaml of a chart, stores at values.yaml
`helm inspect values [chartName] > newValues.yaml`
-- edit the `newValues.yaml` to describe the upgrade
-- deploy the upgrade
`helm upgrade [releaseName] [chartName] -f newValues.yaml` <br>
	5. **clean/remove the release:**<br>
`helm uninstall [releaseName]`

3. ## kubeadm:
	 **kubeadm** is admin tool to setup a cluster
	 1. <br>
	 2. <br>
	
 
4. ## minikube: 
	 **Minikube**: setup & run a single node cluster locally for testing and dev purpose.
	 1.  usage: `minikube -h`
	2.  **usual workflow**:<br>
		`minikube start [computingResourceConfig]`
`minikube status`
`minikube stop`

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTIyMzg1Nzc3LDU4ODE2MzQ4MywxMTM1OT
E1MTM3LDM2NDQ0NTgyNSwtMjA1NzM5NDExMCwxNzEyMDE0MjU5
LC0xODk3MTIwMzcwLDEyNTU2NjIwMzcsNDY5MjM0NTA2LC03MD
UxNTY3NDEsLTQxMTg1NTcwNCw5ODQzNDIzNTMsMjAyNDkzOTE2
NSwxODEyMTM4MDc4LDE3MzU0MjU5ODksLTEzMzM2MTM0OCwtOD
g0MzMyNjQxLDEyNzAxNDE2MzEsMzg4Nzc2MjgwLDY0Mjg3OTQ2
XX0=
-->