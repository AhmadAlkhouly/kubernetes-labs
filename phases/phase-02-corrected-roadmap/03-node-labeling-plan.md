# Node Labeling Plan

## Current Labels

```bash
kubectl get nodes -L workload

k8s-worker-01   workload=web
k8s-worker-02   workload=web
k8s-worker-03   workload=apps
k8s-worker-04   workload=storage

## Target Scheduling
* WordPress Pods  -> workload=web
* MariaDB Pod     -> workload=storage
* Future apps     -> workload=apps
* Storage tools   -> workload=storage

## WordPress nodeSelector
```text
nodeSelector:
  workload: web

## MariaDB nodeSelector
```text
nodeSelector:
  workload: storage

## Important Warning

Because the current StorageClass is local-path, moving MariaDB to another node may break the existing volume attachment if the current PV was created on a different worker node.

Before applying nodeSelector to MariaDB, check:

```text
kubectl get pods -n wordpress -o wide
kubectl get pvc -n wordpress
kubectl get pv


