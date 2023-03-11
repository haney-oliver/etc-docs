---
title: Infrastructure
icon: octicons/gear-24
---

## Setup

All infrastructure is hosted on an Akami/Linode kubernetes cluster.
The kube config can be retrieved [here](https://cloud.linode.com/kubernetes/clusters/96208/summary). There is a link that will allow you to download the `dev-etc-kubeconfig.yaml`. Then run the following to complete your setup:

```bash linenums="1"
# Install the Kubernetes CLI and K9s interface
brew install kubectl derailed/k9s/k9s

# Configure kubectl to connect to the cluster
mv ~/Downloads/dev-etc-kubeconfig.yaml ~/.kube/config

# Validate kubectl and k9s are working as expected
kubectl config use-context lke*****-ctx
kubectl get nodes

k9s --context lke*****-ctx
```
!!! note "Recommendation"
    It is recommended that you provide the context a more logical name to refer to.
    This can be done in your `~/.kube/config`. Edit `contexts[<GENERATED_LINODE_CONTEXT>].name`:
    ```
    name: dev-etc
    ```
    Then you would run the following to refer to the etc cluster context:
    ```bash linenums="1"
    kubectl config use-context dev-etc
    k9s --context dev-etc
    ```

## Infrastructure repositories

Then download the necessary infrastructure and application repositories (application repos are listed [here](../applications/index.md)):

- [orb](https://github.com/haney-oliver/orb)
- [flux](https://github.com/haney-oliver/flux)

All infrastructure services are managed and deployed by [fluxcd](https://github.com/haney-oliver/flux)
Click one of the links below to get more information about a particular service:

- [cert-manager](./cert-manager.md)
- [kube-dashboard](./kube-dashboard.md)
- [kubecost](./kubecost.md)
- [linkerd](./linkerd.md)
- [longhorn](./longhorn.md)
- [mysql](./mysql.md)
- [registry](./registry.md)
- [traefik](./traefik.md)
- [vault](./vault.md)
