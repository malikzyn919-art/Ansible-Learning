# Ansible Inventory Management

## 1. What is Inventory?

An inventory is a file that defines the managed hosts and groups of hosts that Ansible controls.

It tells Ansible which servers to manage.

## 2. Types of Inventory

### Static Inventory
A manually maintained file containing server IP addresses and hostnames.

### Dynamic Inventory
Inventory generated automatically from external sources, such as AWS EC2.

## 3. Default Inventory Location

    /etc/ansible/hosts

A custom inventory can be created anywhere.

Example:

    ~/Ansible-Learning/inventory

## 4. Create a Static Inventory

Example:

    [webservers]
    172.31.27.16 ansible_user=ubuntu

    [dbservers]
    172.31.27.17 ansible_user=ubuntu

These IP addresses are examples. Replace them with your actual managed server IPs.

## 5. Grouping Servers

    [webservers]
    172.31.27.16 ansible_user=ubuntu

    [dbservers]
    172.31.27.17 ansible_user=ubuntu

    [production:children]
    webservers
    dbservers

## 6. Important Inventory Variables

- ansible_host: Actual IP address or hostname.
- ansible_user: SSH username.
- ansible_port: SSH port.
- ansible_ssh_private_key_file: SSH private key path.
- ansible_become: Enable privilege escalation.

Example:

    [webservers]
    web1 ansible_host=172.31.27.16 ansible_user=ubuntu

## 7. Test Inventory

    ansible -i inventory all -m ping

Test only webservers:

    ansible -i inventory webservers -m ping

Test only dbservers:

    ansible -i inventory dbservers -m ping

Display inventory:

    ansible-inventory -i inventory --list

Display groups:

    ansible-inventory -i inventory --graph

## 8. Host and Group Variables

host_vars stores variables for individual hosts.

group_vars stores variables shared by a group.

## 9. Dynamic Inventory

Dynamic inventory can retrieve server information from cloud platforms.

For AWS, Ansible can use the amazon.aws.aws_ec2 inventory plugin.

## 10. Interview Questions

1. What is Ansible inventory?
2. What is static inventory?
3. What is dynamic inventory?
4. What is a host group?
5. What are parent groups?
6. What is group_vars?
7. What is host_vars?
8. How do you test inventory connectivity?

## Summary

Inventory defines which servers Ansible manages and how those servers are grouped.
