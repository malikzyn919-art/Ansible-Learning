# Ansible Playbooks

## 1. What is a Playbook?

An Ansible playbook is a YAML file containing instructions for automating tasks on managed servers.

Unlike ad-hoc commands, playbooks can contain multiple tasks and be reused.

## 2. YAML Basics

YAML uses indentation to organize data.

Example:

    name: Install Nginx
    state: present

Important rules:

- Use spaces, not tabs.
- Maintain consistent indentation.
- Use a colon after keys.
- Lists begin with a hyphen.

## 3. Basic Playbook Structure

    ---
    - name: Configure webserver
      hosts: all
      become: true
      tasks:
        - name: Install nginx
          apt:
            name: nginx
            state: present

## 4. Important Playbook Keywords

### name
Describes a play or task.

### hosts
Defines which inventory hosts will run the play.

### become
Enables privilege escalation.

### become_user
Specifies the user to become, commonly root.

### tasks
Contains the actions Ansible executes.

### gather_facts
Controls automatic collection of host facts.

## 5. Install and Start Nginx

    ---
    - name: Install and start nginx
      hosts: all
      become: true

      tasks:
        - name: Install nginx
          apt:
            name: nginx
            state: present
            update_cache: true

        - name: Start nginx
          service:
            name: nginx
            state: started
            enabled: true

## 6. Run a Playbook

    ansible-playbook -i inventory first-playbook.yml

## 7. Check Playbook Syntax

    ansible-playbook --syntax-check first-playbook.yml

## 8. Dry Run

    ansible-playbook -i inventory first-playbook.yml --check

## 9. Verbose Mode

    ansible-playbook -i inventory first-playbook.yml -v

For more detail:

    ansible-playbook -i inventory first-playbook.yml -vvv

## 10. Limit Execution to a Group

    ansible-playbook -i inventory first-playbook.yml --limit webservers

## 11. Important Concepts

- Play: A set of tasks targeting selected hosts.
- Task: One action in a play.
- Module: Performs the actual operation.
- Playbook: Contains one or more plays.
- Handler: Runs when notified by a task.

## 12. Interview Questions

1. What is an Ansible playbook?
2. What is YAML?
3. What is the purpose of hosts?
4. What does become do?
5. What is the difference between a play and a task?
6. How do you check playbook syntax?
7. What is check mode?
