# WordPress DB Connection Fix

## Issue

WordPress was reachable through NodePort but showed:

```text
Error establishing a database connection

## Checks
* ConfigMap was correct.
* MariaDB Service was correct.
* MariaDB Endpoint was available.
* MariaDB logs showed that the database was ready for connections.

## Fix

The WordPress Deployment was restarted by scaling replicas down to 0 and then back to 2:

kubectl scale deployment wordpress -n wordpress-nfs --replicas=0
kubectl scale deployment wordpress -n wordpress-nfs --replicas=2

## Result
WordPress connected successfully to MariaDB after the pods were recreated.

