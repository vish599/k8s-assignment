# Kubernetes Assignment

This project demonstrates a highly available application deployment in Kubernetes, featuring:

- Multiple replicas for fault tolerance
- Zero-downtime rolling updates
- Health probes for auto-healing
- Resource limits for stability
- Ingress controller for HTTP routing
- StatefulSet database with persistent storage
- Pod Disruption Budget (PDB) for controlled maintenance
- Horizontal Pod Autoscaler (HPA) for automatic scaling


1. Install Helm if not already installed:
```bash
brew install helm

```

2. Install NGINX Ingress Controller using Helm:
```bash

helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx


helm repo update


helm install ingress-nginx ingress-nginx/ingress-nginx \
  --create-namespace \
  --namespace ingress-nginx \
  --values manifests/ingress/values-ingress-nginx.yaml
```

3. Deploy the application:
```bash
kubectl apply -f manifests/database/redis-statefulset.yaml
kubectl apply -f manifests/app/configmap.yaml
kubectl apply -f manifests/app/navatech-assignment.yaml
kubectl apply -f manifests/ingress/ingress.yaml
```

### Final Steps
Access the application at http://navatech-assignment.local


## High Availability Features

- **Fault Tolerance**: Multiple replicas ensure the application remains available if a pod fails
- **Self-Healing**: Automatic restart of unhealthy pods
- **Controlled Disruptions**: Pod Disruption Budget ensures minimum availability during maintenance
- **Auto-Scaling**: Horizontal Pod Autoscaler adjusts replica count based on CPU usage
- **Zero-Downtime Updates**: Rolling update strategy ensures no downtime during deployments
- **Resource Management**: Proper resource requests and limits prevent resource contention
- **Persistent Storage**: Database data persists across pod restarts


