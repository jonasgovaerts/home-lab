# Kubernetes MCP Server - Deployment Manifests

This directory contains Kubernetes manifests to deploy the Kubernetes MCP Server.

## Prerequisites

- A running Kubernetes cluster (e.g., k3s, minikube, EKS, AKS, GKE)
- kubectl configured to access your cluster
- Docker or another container runtime for building/pushing images

## Deployment Steps

### 1. Build and Push the Docker Image

```bash
# Build the Docker image
docker build -t jonas/kubernetes-mcp:latest .

# Push the image to your container registry
docker push jonas/kubernetes-mcp:latest
```

**Note:** Update the image name and tag in `deployment.yaml` if you use a different registry.

### 2. Apply Kubernetes Manifests

Apply all manifests in order:

```bash
kubectl apply -f k8s/service-account.yaml
kubectl apply -f k8s/role.yaml
kubectl apply -f k8s/role-binding.yaml
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

Or apply all at once:

```bash
kubectl apply -f k8s/
```

### 3. Verify Deployment

Check that the pod is running:

```bash
kubectl get pods -l app=kubernetes-mcp-server
```

Check the service:

```bash
kubectl get svc kubernetes-mcp-server
```

View logs:

```bash
kubectl logs -l app=kubernetes-mcp-server
```

### 4. Access the MCP Server

The server will be available at `http://kubernetes-mcp-server.default.svc.cluster.local:8000/mcp` within your cluster.

## Configuration Options

### Custom Image

Edit `deployment.yaml` to change the image:

```yaml
image: your-registry/your-image:tag
```

### Resource Limits

Adjust CPU and memory requests/limits in `deployment.yaml` based on your cluster size.

### Multiple Replicas

For high availability, increase replicas in `deployment.yaml`:

```yaml
replicas: 3
```

## Cleanup

To remove the deployment:

```bash
kubectl delete -f k8s/
```

## Security Notes

- The service account has read-only access to cluster resources
- The server runs with minimal necessary permissions
- Consider using network policies to restrict access if needed
