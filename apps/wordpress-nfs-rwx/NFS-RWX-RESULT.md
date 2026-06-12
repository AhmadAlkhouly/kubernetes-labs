# WordPress NFS RWX Result

## Goal

Enable WordPress to run with multiple replicas across different Kubernetes worker nodes using shared RWX storage.

## Previous Problem

With local-path storage and ReadWriteOnce PVC, WordPress pods could not be safely distributed across multiple nodes.

The local-path volume was tied to a single node.

## New Design

```text
MariaDB:
  replicas: 1
  nodeSelector: workload=storage
  storage: local-path / RWO

WordPress:
  replicas: 2
  nodeSelector: workload=web
  podAntiAffinity: enabled
  storage: NFS / RWX

## Current Result
MariaDB    Running   k8s-worker-04
WordPress  Running   k8s-worker-01
WordPress  Running   k8s-worker-02

## WordPress PVC
wordpress-files   Bound   RWX   nfs-manual

## Conclusion

The NFS RWX volume allowed WordPress pods to run on different worker nodes while sharing the same WordPress files.

This is a correct learning step before moving to more production-like storage solutions such as Longhorn RWX or CephFS.
