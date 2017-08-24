Cluster -> Master:
* All communication paths from the cluster to the master terminate at the apiserver (none of the other master components are designed to expose remote services).

Master -> Cluster:
* apiserver -> kubelet:
  * Fetching logs for pods.
  * Attaching (through kubectl) to running pods
  * Providing the kubelet’s port-forwarding functionality.
* apiserver -> nodes, pods, and services