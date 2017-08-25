A DaemonSet ensures that all (or some) nodes run a copy of a pod. As nodes are added to the cluster, pods are added to them. As nodes are removed from the cluster, those pods are garbage collected. Deleting a DaemonSet will clean up the pods it created.

Some typical uses of a DaemonSet are:
* running a cluster storage daemon, such as glusterd, ceph, on each node.
* running a logs collection daemon on every node, such as fluentd or logstash.
* running a node monitoring daemon on every node, such as Prometheus Node Exporter, collectd, Datadog agent, New Relic agent, or Ganglia gmond.

Communicating with Daemon Pods:
* Push: Pods in the DaemonSet are configured to send updates to another service, such as a stats database. They do not have clients.
* NodeIP and Known Port: Pods in the DaemonSet can use a hostPort, so that the pods are reachable via the node IPs. Clients know the list of node IPs somehow, and know the port by convention.
* DNS: Create a headless service with the same pod selector, and then discover DaemonSets using the endpoints resource or retrieve multiple A records from DNS.
* Service: Create a service with the same pod selector, and use the service to reach a daemon on a random node. (No way to reach specific node.)
