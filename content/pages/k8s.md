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

* Patch a resource (add, e.g. TargetGroupBinding for ALB)
  ```bash
  kubectl -n <namespace> patch targetgroupbinding.elbv2.k8s.aws <resource name> --type=merge --patch <json path to patch>
  ```

* Patch a resource (edit, e.g. affinity / element in array)
  ```bash
  kubectl -n <namespace> patch statefulset <resource name> \
    --type=json \
    -p '[{"op":"replace","path":"/spec/template/spec/affinity/nodeAffinity/requiredDuringSchedulingIgnoredDuringExecution/nodeSelectorTerms/0/matchExpressions/0/values/0","value":"m5.xlarge"}]'
  ```
  See: https://erosb.github.io/post/json-patch-vs-merge-patch/

* Delete all pods in a given namespace
  ```bash
  kubectl -n <namespace> get pod -o Name | xargs -n 1 kubectl -n <namespace> delete $1 --force
  ```

* View events for a particular pod
  ```bash
  kubectl get event -n <namespace> --field-selector involvedObject.name=<pod>
  ```
  
* Decode secret
  ```bash
  kubectl -n <namespace> get secret <secret name> -o jsonpath='{.data.*}' | base64 -d
  ```
