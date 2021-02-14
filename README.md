## datou-k8-argocd-rollouts
---

### Summary
The goal of this project is to provide a guided walkthrough for ArgoCD rollouts. We will explore canary and blue/green deployments.

- [ArgoCD Rollouts](https://github.com/argoproj/argo-rollouts)
- [ArgoCD Rollouts Demo Application](https://github.com/argoproj/rollouts-demo)

### Pre-requisite

You will need a cluster to run the steps in this project. If you are following the datou series, you will need these projects completed.

- datou-k8 - [set up a local cluster](https://github.com/datou-tech/datou-k8)
- datou-k8-helm - [understand helm charts](https://github.com/datou-tech/datou-k8-helm)
- datou-k8-docker - [understand packaging applications](https://github.com/datou-tech/datou-docker)
- datou-k8-argocd - [understand ArgoCD](https://github.com/datou-tech/datou-docker)

### ArgoCD Rollouts
---
### Install ArgoCD Rollouts

1. Install ArgoCD Rollouts
```
kubectl create namespace argo-rollouts
kubectl apply -n argo-rollouts -f https://raw.githubusercontent.com/argoproj/argo-rollouts/stable/manifests/install.yaml

```
2. Install Kubectl ArgoCD Rollouts CLI plugin - `brew install argoproj/tap/kubectl-argo-rollouts`

### Deployments & New Rollout CRD

With ArgoCD Rollouts, there is a new custom resource definition named Rollout. It controls different deployment strategies. This will replace the basic Deployment resource definition.

1. Rolling Updates - deploys new version of your application and terminates old pods in a rolling fashion (use K8 Deployment)
1. Canary Deployments - deploys new version of application to a % of traffic defined by you before either automatically or manually promoting to release to 100% of traffic (use Argo Rollout w/Strategy Canary)
1. Blue/Green Deployments - deploys an entire alternate replicaset of your application side-by-side with a preview of the deployment (use Argo Rollout w/Strategy Blue/Green)

### Deploy Rollouts Demo

1. Deploy the Demo Application
```
    # CLI equivalent command to create
    argocd app create datou-rollout \
    --repo https://github.com/datou-tech/datou-k8-argocd.git \
    --path example-deployment \
    --dest-server https://kubernetes.default.svc \
    --dest-namespace default \
    --sync-policy auto
```

### Canary Deployments

1. Deploy canary resources

### Blue/Green 

1. Deploy blue/green resources

### Istio

1. Upcoming datou-istio project that will tie into deployment strategies with ArgoCD Rollouts
