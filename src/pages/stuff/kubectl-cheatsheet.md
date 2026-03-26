---
layout: '../../layouts/Page.astro'
title: "Kubectl Cheatsheet"
---

## Secrets

List all secrets in a namespace:

```bash
kubectl get secrets -n <namespace>
```

Create secret in specific namespace:

```bash
kubectl create secret generic <secret-name> --from-literal=<key1>='<key1-name>' --from-literal=pwd-'pwd' -n <namespace>
```

## Pods

List all pods in a namespace:

```bash
kubectl get pods -n <namespace>
```

List all pods with a specific label:

```bash
kubectl get pods -n <namespace> -l <label-key>=<label-value>
```

Get YAML configuration for a pod:

```bash
kubectl get pod <pod-name> -n <namespace> -o yaml
```

Connect to pod running e.g. `psql`:

```bash
kubectl exec -it <pod-name> -n <namespace> -- psql -U <username> -d <database>
```
