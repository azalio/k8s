ReplicaSet is the next-generation Replication Controller. The only difference between a ReplicaSet and a Replication Controller right now is the selector support.

While ReplicaSets can be used independently, today it’s mainly used by Deployments as a mechanism to orchestrate pod creation, deletion and updates.

A ReplicaSet ensures that a specified number of pod replicas are running at any given time. 