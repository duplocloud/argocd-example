---
runme:
  id: 01JD0B2NNTMC8PYVHV7ZW088SF
  version: v3
---

# ArgoCD Examples

The following are examples using ArgoCD. This is a POC repo to demonstrate integrating ArgoCD into Duplo.

## Installing ArgoCD

The current instance of ArgoCD is installed using the following terraform module: https://github.com/duplocloud/terraform-kubernetes-addons/tree/argocd

## ArgoCD Projects

A project is a non environmental representation of a collection of applications.

A tenant is the environment that contains the applications deployed by a project and are directly equivalent to a Kubernetes namespace. So each ArgoCD project will have a list of deployable tenants.

Each duplocloud infrastructure can have a project to represent the control-plane applications containing all of the Kubernetes Operators and Controllers.

```sh {"id":"01JD0CVPEJPHYH387QA7VNQ98C","name":"say-hello"}
kubectl apply -f project.yaml
```

## ArgoCD Applications

Each application is defined as a Helm chart or a Kustomize overlay. 

Deploy the demo app: 
```sh
kubectl apply -f env/demo/app.yaml
```
This will watch the `env/demo/values.yaml` file for changes and apply them to the cluster.
