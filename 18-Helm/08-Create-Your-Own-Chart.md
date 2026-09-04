# Create Your Own Helm Chart
Step 1: Create Chart
helm create myapp

Generated structure:

myapp/
├── Chart.yaml
├── values.yaml
└── templates/
Step 2: Configure values.yaml
replicaCount: 2

image:
  repository: nginx
  tag: "latest"

service:
  type: ClusterIP
  port: 80
Step 3: Create Deployment Template
apiVersion: apps/v1
kind: Deployment

metadata:
  name: {{ .Release.Name }}

spec:
  replicas: {{ .Values.replicaCount }}

  selector:
    matchLabels:
      app: {{ .Release.Name }}

  template:
    metadata:
      labels:
        app: {{ .Release.Name }}

    spec:
      containers:
      - name: app
        image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
Step 4: Test Rendering
helm template myapp ./myapp
Step 5: Install
helm install myapp ./myapp

Check:

kubectl get pods
helm list