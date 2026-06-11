# Next Actions

## Step 1: Confirm GitHub Repository Structure

Check:

```bash
tree -a -L 4
git status


## Step 2: Commit the Corrected Roadmap

```bash
git add phases/phase-02-corrected-roadmap
git commit -m "Add corrected Kubernetes lab roadmap"
git push


## Step 3: Review Current WordPress Pods and Volumes

```bash
kubectl get pods -n wordpress -o wide
kubectl get pvc -n wordpress
kubectl get pv

## Step 4: Apply nodeSelector Carefully

* WordPress -> workload=web
* MariaDB -> workload=storage only after checking PV location

## Step 5: Start WordPress Scaling Test

* Create a new lab:

```text
apps/wordpress-scaling-test

### This lab will test:

* WordPress replicas
* ReadWriteOnce limitation
* RWX storage requirement
* NFS or Longhorn integration



