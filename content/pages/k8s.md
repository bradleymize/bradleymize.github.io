---
title: Kubernetes
date: Last Modified 
permalink: /k8s.html
eleventyNavigation:
  key: kubernetes
  title: Kubernetes
---

* List all resources
  ```bash
  kubectl api-resources --verbs=list --namespaced -o name   | xargs -n 1 -I {} sh -c 'echo "====================\nResource: $1\n----------" && kubectl get --show-kind --ignore-not-found -n <namespace> $1' sh {}
  ```

* Patch a resource (e.g. TargetGroupBinding for ALB)
  ```bash
  kubectl -n <namespace> patch targetgroupbinding.elbv2.k8s.aws <resource name> --type=merge --patch <json path to patch>
  ```

* Delete all pods in a given namespace
  ```bash
  kubectl -n <namespace> get pod -o Name | xargs -n 1 kubectl -n <namespace> delete $1 --force
  ```
