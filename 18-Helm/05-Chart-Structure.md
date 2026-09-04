# Helm Chart Structure

myapp/

├── Chart.yaml
├── values.yaml
├── values-dev.yaml
├── values-prod.yaml
├── charts/
└── templates/
    ├── deployment.yaml
    ├── service.yaml
    ├── ingress.yaml
    ├── _helpers.tpl
    └── NOTES.txt
Important Files
Chart.yaml

Contains Chart information.

apiVersion: v2
name: myapp
description: My Kubernetes Application
version: 1.0.0
appVersion: "1.0"
values.yaml

Contains default configuration.

replicaCount: 2

image:
  repository: nginx
  tag: "1.25"

service:
  type: ClusterIP
  port: 80
templates/

Contains Kubernetes YAML templates.

Example:

replicas: {{ .Values.replicaCount }}