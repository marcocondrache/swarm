# Raspberry Pi Cluster Setup with Ansible and k3sup

This directory contains Ansible playbooks for setting up and managing a Raspberry Pi Kubernetes (k3s) cluster.

## Prerequisites

1. Raspberry Pi nodes with SSH access
2. Python installed on all nodes
3. Ansible installed on your control machine

## Inventory

The inventory is defined in `inventory/cluster.yaml` and includes:
- Queen nodes (control plane)
- Worker nodes

## Setting up the k3s Cluster

The setup process includes:

1. Enabling cgroups on all Raspberry Pi nodes
2. Installing k3sup on the control machine
3. Installing k3s on queen nodes
4. Joining worker nodes to the cluster

To set up the cluster, run:

```bash
cd infrastructure
ansible-playbook playbooks/setup_k3s.yaml
```

This will:
- Update the cmdline.txt file on all nodes to enable cgroups and reboot if necessary
- Install k3sup on your local machine
- Use k3sup to install k3s on the queen nodes (first as server, others as server-agents)
- Join all worker nodes to the cluster

## Accessing the Cluster

After successful installation, a kubeconfig file will be created in the project root directory. Use it with:

```bash
export KUBECONFIG=./kubeconfig
kubectl get nodes
```

## Additional Playbooks

- `playbooks/setup.yaml`: Basic setup for all nodes (packages, etc.)

## Notes

- If SSH requires password authentication, add `-k` to the ansible-playbook command
- If sudo requires a password, add `-K` to the ansible-playbook command 