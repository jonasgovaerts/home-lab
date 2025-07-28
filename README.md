# Kubernetes Homelab

This project documents a home lab setup for Kubernetes, leveraging GitOps and automation tools for streamlined management.

## Overview

- **Kubernetes Cluster:** Self-hosted, managed on local hardware.
- **GitOps with Flux:** All cluster configuration and workloads are managed declaratively via [Flux](https://fluxcd.io/).
- **Provisioning with Ansible:** [Ansible](https://www.ansible.com/) is used to install and update Kubernetes nodes.

## Workflow

1. **Provisioning:**  
    Use Ansible playbooks to install Kubernetes and required dependencies on your nodes.

2. **GitOps Deployment:**  
    Flux monitors your Git repository for changes and applies them automatically to the cluster.

3. **Continuous Updates:**  
    Update your infrastructure or workloads by committing changes to your Git repository. Ansible and Flux handle the rest.

## Getting Started

1. Clone this repository.
2. Use the provided Ansible playbooks to set up your Kubernetes cluster.
3. Configure Flux to watch this repository for cluster state.

## Tools Used

- **cert-manager:** Automates the management and issuance of TLS certificates within the Kubernetes cluster. See [cert-manager](https://cert-manager.io/) for more details.
- **external-dns:** Dynamically manages DNS records for Kubernetes resources, ensuring your services are discoverable. Learn more at [external-dns](https://github.com/kubernetes-sigs/external-dns).
- **Traefik:** Acts as an Ingress controller, routing external traffic to services inside the Kubernetes cluster. More information at [Traefik](https://traefik.io/).
- **Rook Ceph:** Provides distributed storage for your Kubernetes cluster using Ceph, enabling block, file, and object storage. See [Rook Ceph](https://rook.io/) for details.
- **authentik:** Offers identity provider and authentication services for your applications and Kubernetes resources. Learn more at [authentik](https://goauthentik.io/).

## Resources

- [Flux Documentation](https://fluxcd.io/docs/)
- [Ansible Documentation](https://docs.ansible.com/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
