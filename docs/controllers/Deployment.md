https://kubernetes.io/docs/concepts/workloads/controllers/deployment/


A Deployment controller provides declarative updates for Pods and ReplicaSets.

You describe a desired state in a Deployment object, and the Deployment controller changes the actual state to the desired state at a controlled rate

Use Case:
* Create a Deployment to rollout a ReplicaSet.
* Declare the new state of the Pods
* Rollback to an earlier Deployment revision
* Scale up the Deployment to facilitate more load.
* Pause the Deployment.
* Use the status of the Deployment.
* Clean up older ReplicaSets.

Deployment status:
* progressing:
  * The Deployment creates a new ReplicaSet.
  * The Deployment is scaling up its newest ReplicaSet.
  * The Deployment is scaling down its older ReplicaSet(s).
  * New Pods become ready or available (ready for at least MinReadySeconds).

* complete:
  * All of the replicas associated with the Deployment have been updated to the latest version you’ve specified, meaning any updates you’ve requested have been completed.
  * All of the replicas associated with the Deployment are available.
  * No old replicas for the Deployment are running.

* stalled:
  * Insufficient quota
  * Readiness probe failures
  * Image pull errors
  * Insufficient permissions
  * Limit ranges
  * Application runtime misconfiguration

Use Cases:
  * Canary Deployment

Strategy:
* Recreate - All existing Pods are killed before new
* RollingUpdate:
  * Max Unavailable (The default value is 25%)
  * Max Surge (The default value is 25%.)
  * Progress Deadline Seconds
  * Min Ready Seconds
  * Rollback To
  * Revision
  * Revision History Limit
  * Paused
  
Alternative to Deployments
* kubectl rolling update
