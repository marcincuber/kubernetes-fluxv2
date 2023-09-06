# kubernetes-fluxv2
Kubernetes- helm deployments using Flux V2

### Fluxv2
[Fluxv2]([https://github.com/fluxcd/flux](https://fluxcd.io/)) is a [Gitops](https://www.weave.works/technologies/gitops/) tool that ensures that a given cluster's state matches what is in git. This allows developers to deploy any new configuration to a cluster by simply commiting to the cluster's directory in this repo. A Flux controller in each cluster polls its designated directory and will apply any new changes once found.

 <img src="https://fluxcd.io/img/diagrams/gitops-toolkit.png">

#### Official FluxV2 docs, install and upgrade instructions

[Flux Docs](https://fluxcd.io/docs/)

```
# install cli
brew install fluxcd/tap/flux
# or
curl -s https://fluxcd.io/install.sh | sudo bash
# check version
flux --version
# upgrade cli
brew upgrade fluxcd/tap/flux
```

```
# bootstrap flux
flux bootstrap github --owner=marcincuber --repository=kubernetes-fluxv2 --path=./ --branch=main --components-extra=image-reflector-controller,image-automation-controller --read-write-key
```

### Deploy Kubernetes Components

I have configured components that I use with EKS that I run. They have all been tested and they work as expected. When re-using them please make sure to configure IAM Role for service accounts which will be specific to your account. Note that not all components require an IAM Role.

- aws-ebs-csi-driver
- aws-load-balancer-controller
- aws-vpc-cni
- cert-manager
- cluster-autoscaler
- external-dns
- external-secrets-operator
- flux
- karpenter
- kube-state-metrics
- kubecost
- kyverno
- metrics-server
- reloader
- seldon-operator
