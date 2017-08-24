A node is a worker machine in Kubernetes.
A node’s status contains the following information:
* Addresses (HostName, ExternalIP, InternalIP)
* The conditions field describes the status of all Running nodes.
`If the Status of the Ready condition is “Unknown” or “False” for longer than the pod-eviction-timeout, 
an argument is passed to the kube-controller-manager and all of the Pods on the node are scheduled for deletion 
by the Node Controller. 
The default eviction timeout duration is five minutes.`

* Capacity describes the resources available on the node: 
  * CPU, 
  * memory 
  * and the maximum number of pods that can be scheduled onto the node.
  
Info:
* General information about the node

Node Controller:
* The first is assigning a CIDR block to the node when it is registered (if CIDR assignment is turned on).
* The second is keeping the node controller’s internal list of nodes up to date with the cloud provider’s list of available machines.
* Monitoring the nodes’ health.