---
id: Extra tooling
aliases: []
tags:
  - kubernetes
  - servers
created: "20250127-1500"
---
## Flux

To manage Kubernetes clusters by applying GitOps

``` bash
curl -s https://fluxcd.io/install.sh | sudo bash
```

### Bootstrap Flux with a new github repo

``` bash
flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=nova-rhel-kubernetes \
  --branch=main \
  --path=clusters/nova-rhel-cluster \
  --personal
```

## Kubeseal

To encrypt secrets from the Kubernetes cluster, so they are easily managed by Flux without worrying about them

``` bash
KUBESEAL_VERSION='' # Set this to, for example, KUBESEAL_VERSION='0.23.0'
curl -OL "https://github.com/bitnami-labs/sealed-secrets/releases/download/v${KUBESEAL_VERSION:?}/kubeseal-${KUBESEAL_VERSION:?}-linux-amd64.tar.gz"
tar -xvzf kubeseal-${KUBESEAL_VERSION:?}-linux-amd64.tar.gz kubeseal
sudo install -m 755 kubeseal /usr/local/bin/kubeseal
```

---
## Related Ideas
* [[permanent]]


## Sources

https://fluxcd.io/flux/installation/#install-the-flux-cli
https://github.com/bitnami-labs/sealed-secrets
