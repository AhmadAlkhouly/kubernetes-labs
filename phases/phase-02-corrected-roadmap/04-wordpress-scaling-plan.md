# WordPress Scaling Plan

## Current State

```text
MariaDB replicas: 1
WordPress replicas: 1
Storage: local-path / ReadWriteOnce

## Why MariaDB Should Not Be Scaled Directly

Do not run:

kubectl scale deployment mariadb -n wordpress --replicas=2

### This does not create database replication.

#### It may cause:

* Data inconsistency
* PVC conflicts
* Multiple independent database instances
* WordPress reading and writing from different database states

#### Why WordPress Cannot Be Scaled Yet

The current WordPress PVC uses ReadWriteOnce storage.

If WordPress is scaled to 2 replicas, the second pod may fail because both pods need access to the same WordPress files.

## Correct Next Step

** Before scaling WordPress:

1. Add RWX storage.
2. Use NFS or Longhorn.
3. Move WordPress files to shared storage.
4. Keep MariaDB as replicas=1.
5. Scale WordPress to replicas=2.
6. Test uploads, plugins, and themes.

## Future Production-like Design

* WordPress replicas: 2+
* MariaDB: external DB or HA database cluster
* Storage: NFS / Longhorn RWX / Object Storage
* Ingress: NGINX Ingress
* Cache: Redis
* CDN: Cloudflare
* Backup: scheduled
* Monitoring: Prometheus + Grafana


