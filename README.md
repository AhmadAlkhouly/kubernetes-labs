# Kubernetes Labs

A collection of hands-on Kubernetes labs for learning real-world deployments, storage, scaling, and GitOps.

## Current Projects

### WordPress Basic

Path:

```text
apps/wordpress-basic


# Kubernetes WordPress Lab

This lab deploys **WordPress with MariaDB** on Kubernetes using basic Kubernetes resources and local storage.

## Lab Components

This lab includes:

- Namespace
- Deployments
- Services
- PVCs
- Secret template
- ConfigMap
- local-path StorageClass

## Planned Labs

The following labs are planned as part of the Kubernetes learning path:

- WordPress with shared storage
- WordPress with Ingress and SSL
- WordPress production-like setup
- Odoo basic deployment
- Odoo with PostgreSQL and custom addons
- Kubernetes HA cluster with 3 control-plane nodes
- Longhorn storage
- Monitoring with Prometheus and Grafana
- GitOps with Argo CD

## Security Notice

Do **not** commit real secrets to Git.

Use `.local.yaml` files for local credentials and keep only `.example.yaml` templates in Git.

Example:

```text
secret.local.yaml      # Local only, do not commit
secret.example.yaml    # Safe template, can be committed
```

## Recommended Git Ignore

Add local secret files to `.gitignore`:

```gitignore
*.local.yaml
.env
```
---

## 4. تهيئة Git من جذر الريبو

من داخل:

```bash
~/k8s-projects/kubernetes-labs
