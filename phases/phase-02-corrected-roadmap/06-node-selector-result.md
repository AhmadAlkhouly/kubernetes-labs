# Node Selector Result

## Goal

Run WordPress on web nodes and MariaDB on the storage node.

## Node Labels

```text
k8s-worker-01   workload=web
k8s-worker-02   workload=web
k8s-worker-03   workload=apps
k8s-worker-04   workload=storage

## Applied Scheduling
WordPress -> workload=web
MariaDB   -> workload=storage

## Current Result
mariadb    Running   k8s-worker-04
wordpress  Running   k8s-worker-02

## Storage
mariadb-data      Bound   RWO   local-path
wordpress-files   Bound   RWO   local-path


## Note:
The current storage uses local-path and ReadWriteOnce.

This is suitable for the current single-replica lab.

WordPress should not be scaled yet until RWX storage is added.

MariaDB should remain `replicas=1` unless a real database replication solution is implemented.


