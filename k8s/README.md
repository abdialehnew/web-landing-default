# ArgoCD Deployment for HTML Landing Page

This directory contains Kubernetes manifests for deploying the HTML landing page using ArgoCD.

## Files

- `application.yaml`: ArgoCD Application manifest that defines how ArgoCD should deploy the application
- `configmap.yaml`: ConfigMap containing the HTML content
- `deployment.yaml`: Kubernetes Deployment that runs the nginx container with the HTML content
- `service.yaml`: Kubernetes Service that exposes the deployment
- `kustomization.yaml`: Kustomize configuration that organizes all resources

## Deployment Instructions

1. Make sure ArgoCD is installed in your Kubernetes cluster
2. Apply the ArgoCD Application manifest:

```bash
kubectl apply -f application.yaml
```

3. ArgoCD will automatically sync and deploy the application to the default namespace

## Configuration

- The application is deployed to the `default` namespace
- The deployment uses 2 replicas for high availability
- The HTML content is stored in a ConfigMap and mounted into the nginx container
- The service exposes the application on port 80

## Accessing the Application

After deployment, the application will be available at:

```
http://<cluster-ip>:<node-port>/
```

Or if you have an Ingress controller:

```
http://html-landing.<your-domain>/
```

## Troubleshooting

If you encounter issues with the deployment:

1. Check the ArgoCD UI for sync status and errors
2. Verify that the pods are running:

```bash
kubectl get pods -n default -l app=html-landing
```

3. Check the logs of the pods:

```bash
kubectl logs -n default -l app=html-landing
```