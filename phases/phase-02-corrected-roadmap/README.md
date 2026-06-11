# Phase 02: Corrected Roadmap

This phase documents the corrected execution order before continuing with advanced Kubernetes labs.

## Current Status

The current Kubernetes cluster is a single-master lab cluster with four worker nodes.

```text
k8s-master-01   control-plane
k8s-worker-01   workload=web
k8s-worker-02   workload=web
k8s-worker-03   workload=apps
k8s-worker-04   workload=storage

## Current Application (Start Point)

** The current application is: apps/wordpress-basic
### It includes:

1. WordPress Deployment
2. MariaDB Deployment
3. WordPress Service
3. MariaDB Service
4. PVC for WordPress files
5. PVC for MariaDB data
6. Secret example file
7. ConfigMap
8. local-path StorageClass

### Corrected Execution Order

** The corrected order is:
1. Organize the current code in GitHub.
2. Document the current single-master cluster.
3. Use node labels and node selectors.
4. Test WordPress scaling limitations.
5. Add RWX storage using NFS or Longhorn.
6. Scale WordPress correctly.
7. Add Ingress.
8. Add monitoring and backup.
9. Later, build a separate HA cluster with 3 control-plane nodes.
10. Later, use GitOps with Argo CD.


