# Ansible Roles

## 1. What is an Ansible Role?

A role is a structured way to organize Ansible automation into reusable components.

Roles help organize tasks, handlers, variables, templates, files, and metadata.

## 2. Why Use Roles?

- Reusability
- Better organization
- Easier maintenance
- Separation of responsibilities
- Easier collaboration

## 3. Create a Role

    ansible-galaxy role init nginx

## 4. Role Directory Structure

    nginx/
    ├── defaults/
    │   └── main.yml
    ├── files/
    ├── handlers/
    │   └── main.yml
    ├── meta/
    │   └── main.yml
    ├── tasks/
    │   └── main.yml
    ├── templates/
    ├── tests/
    └── vars/
        └── main.yml

## 5. Important Directories

### tasks/
Contains tasks executed by the role.

### handlers/
Contains handlers used by the role.

### defaults/
Contains default variables with lower precedence.

### vars/
Contains role variables with higher precedence than defaults.

### files/
Contains static files that can be copied to managed nodes.

### templates/
Contains Jinja2 templates.

### meta/
Contains role metadata and dependencies.

### tests/
Can contain tests and example inventory files.

## 6. Example Role Task

nginx/tasks/main.yml:

    ---
    - name: Install nginx
      apt:
        name: nginx
        state: present
      become: true

    - name: Start nginx
      service:
        name: nginx
        state: started
        enabled: true
      become: true

## 7. Use a Role in a Playbook

    ---
    - name: Configure webservers
      hosts: all
      become: true

      roles:
        - nginx

## 8. Run the Playbook

    ansible-playbook -i inventory site.yml

## 9. Ansible Galaxy

Ansible Galaxy is a community platform for sharing and downloading Ansible roles and collections.

Initialize a role:

    ansible-galaxy role init nginx

Install a role:

    ansible-galaxy role install username.rolename

## 10. Interview Questions

1. What is an Ansible role?
2. Why do we use roles?
3. What is the difference between defaults and vars?
4. What is the purpose of handlers?
5. What is Ansible Galaxy?
6. What is role reuse?
