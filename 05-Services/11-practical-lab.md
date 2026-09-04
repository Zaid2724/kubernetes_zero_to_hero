🧪 Practical Lab

Use this simple Deployment:

apiVersion: apps/v1
kind: Deployment

metadata:
  name: nginx-deployment

spec:
  replicas: 3

  selector:
    matchLabels:
      app: nginx

  template:
    metadata:
      labels:
        app: nginx

    spec:
      containers:
        - name: nginx
          image: nginx:1.27
          ports:
            - containerPort: 80

Create it:

kubectl apply -f deployment.yaml

Create a ClusterIP Service:

apiVersion: v1
kind: Service

metadata:
  name: nginx-service

spec:
  selector:
    app: nginx

  ports:
    - port: 80
      targetPort: 80

  type: ClusterIP

Apply:

kubectl apply -f service.yaml

Verify:

kubectl get pods
kubectl get svc
kubectl get endpoints

The complete request flow is:

Client
   ↓
nginx-service
   ↓
Selector: app=nginx
   ↓
Deployment Pods
   ├── nginx Pod 1
   ├── nginx Pod 2
   └── nginx Pod 3

