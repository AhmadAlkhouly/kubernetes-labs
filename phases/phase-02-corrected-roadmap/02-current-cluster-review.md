# Current Cluster Review

## Cluster Type

This is a kubeadm-based single-master Kubernetes lab cluster.

## Nodes

```text
k8s-master-01   192.168.70.230   control-plane
k8s-worker-01   192.168.70.234   workload=web
k8s-worker-02   192.168.70.235   workload=web
k8s-worker-03   192.168.70.236   workload=apps
k8s-worker-04   192.168.70.237   workload=storage

## Network

All nodes are running on VMware using Bridged Network.

##Kubernetes Components

* Kubernetes: v1.36.1
* Container Runtime: containerd
* CNI: Calico
* StorageClass: local-path

## Current Limitations

* Single control-plane node.
* No API Server HA.
* local-path storage is node-local.
* WordPress cannot be safely scaled yet.
* MariaDB cannot be scaled by simply increasing Deployment replicas.

## Current Purpose

This cluster is suitable for learning, testing, and building Kubernetes portfolio labs.
It is not yet a production-ready HA cluster.


