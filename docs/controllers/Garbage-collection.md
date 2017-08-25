https://kubernetes.io/docs/concepts/workloads/controllers/garbage-collection/

The role of the Kubernetes garbage collector is to delete certain objects that once had an owner, but no longer have an owner.

Additional note on Deployments
When using cascading deletes with Deployments you must use propagationPolicy: Foreground to delete not only the ReplicaSets created, but also their Pods. If this type of propagationPolicy is not used, only the ReplicaSets will be deleted, and the Pods will be orphaned. See kubeadm/#149 for more information.
