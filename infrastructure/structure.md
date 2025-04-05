# Ansible project structure

```
infrastructure/
├── inventory/                   # Inventory files
│   ├── cluster.yaml             # Your existing inventory
│   └── group_vars/              # Variables for groups
│       ├── all.yaml             # Variables for all hosts
│       ├── queens.yaml          # Variables for queen nodes
│       └── workers.yaml         # Variables for worker nodes
│
├── playbooks/                   # Folder containing playbooks
│   ├── setup.yaml               # Initial setup playbook
│   ├── maintenance.yaml         # Maintenance tasks
│   └── applications/            # Application-specific playbooks
│       ├── kubernetes.yaml
│       └── monitoring.yaml
│
├── roles/                       # Reusable roles
│   ├── common/                  # Common configurations
│   ├── queens/                  # Queen node specific role
│   └── workers/                 # Worker node specific role
│
└── ansible.cfg                  # Ansible configuration
```