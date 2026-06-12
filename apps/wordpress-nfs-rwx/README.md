# WordPress Basic on Kubernetes

This project deploys a basic WordPress application on Kubernetes using MariaDB as the database backend.

## Components

- Namespace: `wordpress`
- Deployment: `wordpress`
- Deployment: `mariadb`
- Service: `wordpress`
- Service: `mariadb`
- PersistentVolumeClaim: `wordpress-files`
- PersistentVolumeClaim: `mariadb-data`
- Secret: database credentials
- ConfigMap: WordPress configuration
- StorageClass: `local-path`

## Project Structure

```text
wordpress-basic/
├── 00-namespace.yaml
├── 01-secret.example.yaml
├── 01-secret.local.yaml
├── 02-configmap.yaml
├── 03-mariadb-pvc.yaml
├── 04-wordpress-pvc.yaml
├── 05-mariadb.yaml
├── 06-wordpress.yaml
├── .gitignore
└── README.md
