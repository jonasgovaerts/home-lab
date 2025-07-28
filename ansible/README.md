# Ansible Kubernetes Playbooks

This repository contains Ansible playbooks to **install**, **destroy**, and **update** a Kubernetes cluster.

## Prerequisites

- Ansible installed on your control machine
- SSH access to all target nodes
- Inventory file configured with your hosts

## Networking

This setup uses **Cilium** as the CNI (Container Network Interface) for Kubernetes networking. BGP is leveraged to provide IP addresses for `Service` resources of type `LoadBalancer`.

## Usage

### 1. Install Kubernetes

```sh
ansible-playbook -i inventory.yaml install-kubernetes.yml
```

### 2. Update Kubernetes

```sh
ansible-playbook -i inventory.yaml update-kubernetes.yml
```

### 3. Destroy Kubernetes

```sh
ansible-playbook -i inventory.yaml destroy-kubernetes.yml
```

## Playbook Overview

- `install-kubernetes.yml`: Installs and configures Kubernetes on your nodes.
- `update-kubernetes.yml`: Updates Kubernetes components to the latest version.
- `destroy-kubernetes.yml`: Removes Kubernetes and cleans up resources.

## Notes

- Review each playbook and adjust variables as needed.
- Ensure you have backups before running destructive actions.
