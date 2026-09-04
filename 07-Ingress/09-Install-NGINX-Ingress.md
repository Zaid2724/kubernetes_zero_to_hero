# Installing an Ingress Controller

Before creating an Ingress resource,
an Ingress Controller must exist.

Check:

kubectl get ingressclass

Check controller:

kubectl get pods -A | grep ingress

After installation, check:

kubectl get svc -A

The controller may be exposed using:

LoadBalancer
NodePort

In cloud environments, the controller is commonly
accessible through a cloud Load Balancer.