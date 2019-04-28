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
1. **LoadBl**
1. **NodePort**
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg4NTAyMDkxOCwyNzc0NzkzNTcsLTEwNT
Y0NDI3Miw3ODkxNzM0OTMsMTM2MDU3Mjc2MCwxNjY1MTU0Nzgy
LC0yMjExMjkyNTQsLTIyNTA0NjQzOSw4Mjc4NTM4NTZdfQ==
-->