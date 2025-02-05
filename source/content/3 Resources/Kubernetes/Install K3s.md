---
id: Install K3s
aliases: []
tags:
  - kubernetes,
  - servers
created: "20250127-1500"
---

Supose you are in a new server and you want to install k3s in it.

# Goals

1. Simplify regular server and new server deployments
2. Configuration with off-the-shelf tools
3. Secrets management

## Prerequisites

Documentation says to disable the firewall. That's preposterous!

It also has rules to allow k3s ports which are much better:

```bash
#RHEL
firewall-cmd --permanent --add-port=6443/tcp #apiserver
firewall-cmd --permanent --zone=trusted --add-source=10.42.0.0/16 #pods
firewall-cmd --permanent --zone=trusted --add-source=10.43.0.0/16 #services
firewall-cmd --reload

#Ubuntu ufw
ufw allow 6443/tcp #apiserver
ufw allow from 10.42.0.0/16 to any #pods
ufw allow from 10.43.0.0/16 to any #services
```

# Install script

``` bash
curl -sfL https://get.k3s.io | sh -
```

## Copy kubeconfig for normal user

```bash
mkdir -p ~/.kube \
  && sudo cp /etc/rancher/k3s/k3s.yaml ~/.kube/config \
  && sudo chown $(id -u):$(id -g) ~/.kube/config
  && export KUBECONFIG=$HOME/.kube/config
```

## Inspect the cluster

```bash
kubectl get nodes
kubectl get pods -A
```


---
## Related Ideas
* [[permanent]]
* check [[Extra tooling]]


## Sources

https://youtu.be/ePyFJ7Hd57Q

