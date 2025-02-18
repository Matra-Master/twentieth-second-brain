---
created: "20250214-1509"
tags:
  - Resources/kubernetes
---

## Network model concepts
- Each *pod* has it's own cluster IP
   - A pod has it's own private network which is shared by every container inside
   - Processes from a *container* refer to processes in another container as **localhost**
- There's a *pod network* that handles communications between pods.
   - All pods can comunicate with all other pods, whether on the same node or **different nodes**.


---

## Sources

https://kubernetes.io/docs/concepts/services-networking/
