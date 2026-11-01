# Ansible Conditionals and Loops

## 1. What are Conditionals?

Conditionals allow Ansible to execute tasks only when a specified condition is true.

Ansible commonly uses the when keyword.

## 2. Example: Install Nginx Only on Ubuntu

    - name: Install nginx on Ubuntu
      apt:
        name: nginx
        state: present
      when: ansible_distribution == "Ubuntu"
      become: true

## 3. Check Multiple Conditions

    when:
      - ansible_distribution == "Ubuntu"
      - ansible_os_family == "Debian"

## 4. What are Loops?

Loops allow Ansible to repeat a task for multiple items.

## 5. Install Multiple Packages

    - name: Install packages
      apt:
        name: "{{ item }}"
        state: present
      loop:
        - nginx
        - git
        - curl
      become: true

## 6. Create Multiple Users

    - name: Create users
      user:
        name: "{{ item }}"
        state: present
      loop:
        - ali
        - ahmed
        - zain
      become: true

## 7. Loop Over Dictionaries

    users:
      - name: ali
        shell: /bin/bash
      - name: ahmed
        shell: /bin/bash

    tasks:
      - name: Create users
        user:
          name: "{{ item.name }}"
          shell: "{{ item.shell }}"
          state: present
        loop: "{{ users }}"
        become: true

## 8. Common Loop Concepts

- loop
- item
- loop_control
- loop_var
- when

## 9. Interview Questions

1. What is a conditional?
2. What is the when keyword?
3. What is a loop?
4. What is item?
5. How do you install multiple packages?
6. Can you combine loops and conditionals?
