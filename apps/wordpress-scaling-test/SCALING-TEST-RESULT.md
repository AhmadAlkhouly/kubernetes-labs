# WordPress Scaling Test Result

## Test Goal

Test whether WordPress can be scaled to multiple replicas using the current local-path StorageClass and ReadWriteOnce PVC.

## Current Design

```text
MariaDB replicas: 1
WordPress replicas: 2+
StorageClass: local-path
AccessMode: ReadWriteOnce
WordPress nodeSelector: workload=web
MariaDB nodeSelector: workload=storage

## Node Labels
k8s-worker-01   workload=web
k8s-worker-02   workload=web
k8s-worker-03   workload=apps
k8s-worker-04   workload=storage

## Test Result
Some WordPress pods were able to run on the same node where the local-path volume was created.

However, after adding pod anti-affinity to force WordPress pods to run on different nodes, one pod remained Pending.

## Observed Scheduling Error
0/5 nodes are available:
1 node(s) didn't match PersistentVolume's node affinity,
1 node(s) didn't match pod anti-affinity rules,
1 node(s) had untolerated taint,
2 node(s) didn't match Pod's node affinity/selector.

## Explanation

The WordPress PVC uses local-path storage with ReadWriteOnce access mode.

The local-path volume is tied to a specific node. When Kubernetes tries to schedule another WordPress pod on a different web node, the pod cannot use the same volume because the volume is not shared across nodes.

## Conclusion

This is not a correct multi-node WordPress scaling design.

WordPress needs shared RWX storage before it can be safely scaled across multiple Kubernetes nodes.

## Next Step

Add RWX shared storage using one of the following:

* NFS
* Longhorn RWX
* CephFS

For the next lab, we will start with NFS because it is easier to understand and suitable for learning.


