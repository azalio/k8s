Server components:
* **kube-apiserver** exposes the Kubernetes API. It is the front-end for the Kubernetes control plane. It is designed to scale horizontally – that is, it scales by deploying more instances.
* **etcd** is used as Kubernetes’ backing store. All cluster data is stored here. Always have a backup plan for etcd’s data for your Kubernetes cluster.
* **kube-controller-manager** runs controllers, which are the background threads that handle routine tasks in the cluster.
  * Node Controller: Responsible for noticing and responding when nodes go down.
  * Replication Controller: Responsible for maintaining the correct number of pods for every replication controller object in the system.
  * Endpoints Controller: Populates the Endpoints object (that is, joins Services & Pods).
  * Service Account & Token Controllers: Create default accounts and API access tokens for new namespaces.
* **cloud-controller-manager** runs controllers that interact with the underlying cloud providers. The cloud-controller-manager binary is an alpha feature introduced in Kubernetes release 1.6.
```cloud-controller-manager runs cloud-provider-specific controller loops only. You must disable these controller loops in the kube-controller-manager. You can disable the controller loops by setting the --cloud-provider flag to external when starting the kube-controller-manager.```
* **kube-scheduler** watches newly created pods that have no node assigned, and selects a node for them to run on.
* addons
  * `Namespaced addon objects are created in the kube-system namespace.`
    * **DNS** 
    * **User interface**, The kube-ui provides a read-only overview of the cluster state.
    * **Container Resource Monitoring**, records generic time-series metrics about containers in a central database, and provides a UI for browsing that data.
    * **Cluster-level Logging** mechanism is responsible for saving container logs to a central log store with search/browsing interface.

Node components:
  * **kubelet** is the primary node agent. It watches for pods that have been assigned to its node (either by apiserver or via local configuration file)
    * Mounts the pod’s required volumes.
    * Downloads the pod’s secrets.
    * Runs the pod’s containers via docker (or, experimentally, rkt).
    * Periodically executes any requested container liveness probes.
    * Reports the status of the pod back to the rest of the system, by creating a mirror pod if necessary.
    * Reports the status of the node back to the rest of the system.

  * **kube-proxy** enables the Kubernetes service abstraction by maintaining network rules on the host and performing connection forwarding.
  * **docker** is used for running containers.
  * **rkt** is supported experimentally for running containers as an alternative to docker.
  * **supervisord** is a lightweight process monitor and control system that can be used to keep kubelet and docker running.
  * **fluentd** is a daemon which helps provide cluster-level logging.