# Helm Repositories

A Helm repository stores and distributes Charts.

Basic workflow:

Repository
    ↓
Search Chart
    ↓
Install Chart

Add repository:

helm repo add bitnami https://charts.bitnami.com/bitnami

Update repositories:

helm repo update

Search:

helm search repo nginx

Install:

helm install my-nginx bitnami/nginx

List repositories:

helm repo list