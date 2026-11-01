# Ansible Variables

## 1. What are Variables?

Variables store values that can be reused in playbooks and roles.

They make automation flexible and reusable.

## 2. Define Variables in a Playbook

    ---
    - name: Variable example
      hosts: all
      vars:
        package_name: nginx

      tasks:
        - name: Install package
          apt:
            name: "{{ package_name }}"
            state: present
          become: true

## 3. Variables in a Separate File

Create vars.yml:

    package_name: nginx
    service_name: nginx

Use it in a playbook:

    vars_files:
      - vars.yml

## 4. Variables in Inventory

    [webservers:vars]
    ansible_user=ubuntu
    environment=production

## 5. Host Variables

host_vars/web1.yml:

    environment: production

## 6. Group Variables

group_vars/webservers.yml:

    package_name: nginx

## 7. Register Variables

Register captures the output of a task.

    - name: Check disk space
      command: df -h
      register: disk_output

    - name: Display disk output
      debug:
        var: disk_output.stdout

## 8. Facts

Facts are system information automatically collected by Ansible.

Examples:

- Operating system
- IP addresses
- Memory
- CPU
- Hostname

Display facts:

    ansible all -i inventory -m setup

Disable fact gathering:

    gather_facts: false

## 9. Variable Precedence

Ansible has multiple variable sources and precedence levels.

In general, extra variables supplied with -e have very high precedence.

Example:

    ansible-playbook site.yml -e "package_name=nginx"

Consult Ansible's variable precedence documentation when resolving conflicts.

## 10. Interview Questions

1. What are Ansible variables?
2. How do you define variables?
3. What are group_vars?
4. What are host_vars?
5. What is register?
6. What are Ansible facts?
7. What is variable precedence?
8. What is the purpose of the debug module?
