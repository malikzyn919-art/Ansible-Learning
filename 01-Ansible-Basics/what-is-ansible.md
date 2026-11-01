# What is Ansible?

Ansible is an open-source automation tool used for:

- Configuration management
- Application deployment
- Infrastructure automation
- Server management

## Important Components

1. Control Node
2. Managed Nodes
3. Inventory
4. Modules
5. Playbooks
6. Roles

## Important Commands

Check Ansible version:

    ansible --version

Test connection:

    ansible -i inventory all -m ping

Check server uptime:

    ansible -i inventory all -m command -a "uptime"
