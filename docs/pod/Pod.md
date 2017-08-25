https://kubernetes.io/docs/user-guide/kubectl-cheatsheet/

https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/
**pod-lifecycle**:

* **Pending**: The Pod has been accepted by the Kubernetes 
system, but one or more of the Container images has 
not been created. This includes time before being 
scheduled as well as time spent downloading images 
over the network, which could take a while.

* **Running**: The Pod has been bound to a node, 
and all of the Containers have been created. 
At least one Container is still running, or is in 
the process of starting or restarting.

* **Succeeded**: All Containers in the Pod have terminated in success, 
and will not be restarted.

* **Failed**: All Containers in the Pod have terminated, 
and at least one Container has terminated in failure. 
That is, the Container either exited with non-zero 
status or was terminated by the system.

* **Unknown**: For some reason the state of the Pod 
could not be obtained, typically due to an error 
in communicating with the host of the Pod.

`$ kubectl get pod test-pod --template={{.status.phase}}
Running`

In general, Pods do not disappear until someone destroys them. This might be a human or a controller. The only exception to this rule is that Pods with a phase of Succeeded or Failed for more than some duration (determined by the master) will expire and be automatically destroyed.
Three types of controllers are available:

* Use a **Job** for Pods that are expected to terminate, for example, batch computations. Jobs are appropriate only for Pods with restartPolicy equal to OnFailure or Never.
* Use a **ReplicationController**, ReplicaSet, or Deployment for Pods that are not expected to terminate, for example, web servers. ReplicationControllers are appropriate only for Pods with a restartPolicy of Always.
* Use a **DaemonSet** for Pods that need to run one per machine, because they provide a machine-specific system service.

https://kubernetes.io/docs/concepts/workloads/pods/init-containers/
* Init Containers are exactly like regular Containers, except:
* They always run to completion.
* Each one must complete successfully before the next one is started.

https://kubernetes.io/docs/concepts/workloads/pods/disruptions/
* An Application Owner can create a PodDisruptionBudget object (PDB) for each application. A PDB limits the number pods of a replicated application that are down simultaneously from voluntary disruptions. 



