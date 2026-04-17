# Kubernetes Homelab

This project documents a home lab setup for Kubernetes, leveraging GitOps and automation tools for streamlined management.

## Overview

- **Kubernetes Cluster:** Self-hosted, managed on local hardware.
- **GitOps with ArgoCD:** All cluster configuration and workloads are managed declaratively via [ArgoCD](https://argoproj.github.io/cd/).
- **Provisioning with Ansible:** [Ansible](https://www.ansible.com/) is used to install and update Kubernetes nodes.

## Workflow

1. **Provisioning:**  
    Use Ansible playbooks to install Kubernetes and required dependencies on your nodes.

2. **GitOps Deployment:**  
    ArgoCD monitors your Git repository for changes and applies them automatically to the cluster.

3. **Continuous Updates:**  
    Update your infrastructure or workloads by committing changes to your Git repository. Ansible and ArgoCD handle the rest.

## Getting Started

1. Clone this repository.
2. Use the provided Ansible playbooks to set up your Kubernetes cluster.
3. Configure ArgoCD to watch this repository for cluster state.

## Tools Used

- **cert-manager:** Automates the management and issuance of TLS certificates within the Kubernetes cluster. See [cert-manager](https://cert-manager.io/) for more details.
- **external-dns:** Dynamically manages DNS records for Kubernetes resources, ensuring your services are discoverable. Learn more at [external-dns](https://github.com/kubernetes-sigs/external-dns).
- **Traefik:** Acts as an Ingress controller, routing external traffic to services inside the Kubernetes cluster. More information at [Traefik](https://traefik.io/).
- **Longhorn:** Provides highly available persistent storage for your Kubernetes cluster. See [Longhorn](https://longhorn.io/) for details.
- **authentik:** Offers identity provider and authentication services for your applications and Kubernetes resources. Learn more at [authentik](https://goauthentik.io/).

## Resources

- [ArgoCD Documentation](https://argo-cd.readthedocs.io/en/stable/)
- [Ansible Documentation](https://docs.ansible.com/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)


## OIDC Authentication with authentik

To authenticate against your Kubernetes cluster using OIDC with authentik, configure `kubectl-oidc-login`:

```bash
kubectl oidc-login setup \
  --oidc-issuer-url=<ISSUER_URL> \
  --oidc-client-id=<CLIENT_ID> \
  --oidc-client-secret=<CLIENET_SECRET> \
  --oidc-extra-scope=openid,email,profile,groups,nickname
```
