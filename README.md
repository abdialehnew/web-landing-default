# web-landing-default
Template Default One Page using HTML, CSS, and JavaScript

## Deployment

This project includes deployment configuration for Kubernetes using ArgoCD. See the [k8s directory](./k8s) for deployment files and instructions.

to deploy the application using ArgoCD CLI, you can use the following command
Log in to ArgoCD CLI:
```bash
argocd login <ARGOCD_SERVER> --username <USERNAME> --password <PASSWORD> --insecure
```

Then create the application:
```bash
argocd app create landing-default --repo https://github.com/abdialehnew/web-landing-default.git --path k8s --dest-server https://kubernetes.default.svc --dest-namespace default
argocd app sync landing-default
```
if ArgoCD is not installed, you can follow the [ArgoCD installation guide](https://argo-cd.readthedocs.io/en/stable/getting_started/).