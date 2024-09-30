# ☸️ Kubernetes

install MicroK8s to run Kubernetes on ubuntu: https://microk8s.io/

## Terminology
- Pod: One or more containers running together on one node - basic unit of deployment. Containers are always in pods
- Controller: For creating/updating pods and other objects - many types (Deployment, ReplicaSet, StatefulSet, DaemonSet, Job, CronJob, ...)
- Service: Network endpoint to connect to a pod
- Namespace: Filtered group of objects in cluster
