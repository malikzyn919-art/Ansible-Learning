# Ansible Ad-hoc Commands

## 1. What are Ad-hoc Commands?

Ad-hoc commands are single Ansible commands used to perform quick tasks without writing a playbook.

They are useful for testing, troubleshooting, and simple administration.

## 2. General Syntax

    ansible <hosts> -i <inventory> -m <module> -a "<arguments>"

## 3. Test Connectivity

    ansible -i inventory all -m ping

## 4. Check Server Uptime

    ansible -i inventory all -m command -a "uptime"

## 5. Check Disk Space

    ansible -i inventory all -m command -a "df -h"

## 6. Check Memory

    ansible -i inventory all -m command -a "free -h"

## 7. Check CPU Information

    ansible -i inventory all -m command -a "nproc"

## 8. Install Nginx

    ansible -i inventory all -b -m apt -a "name=nginx state=present"

## 9. Start Nginx

    ansible -i inventory all -b -m service -a "name=nginx state=started"

## 10. Stop Nginx

    ansible -i inventory all -b -m service -a "name=nginx state=stopped"

## 11. Create a File

    ansible -i inventory all -m file -a "path=/home/ubuntu/test.txt state=touch"

## 12. Create a Directory

    ansible -i inventory all -m file -a "path=/home/ubuntu/devops state=directory"

## 13. Copy a File

    ansible -i inventory all -m copy -a "src=hello.txt dest=/home/ubuntu/hello.txt"

## 14. Delete a File

    ansible -i inventory all -m file -a "path=/home/ubuntu/test.txt state=absent"

## 15. Important Options

- -i: Specify inventory.
- -m: Specify module.
- -a: Pass module arguments.
- -b: Enable privilege escalation.
- -u: Specify remote user.
- -K: Ask for sudo password.
- -v: Verbose output.

## 16. Important Modules

- ping
- command
- shell
- apt
- yum
- file
- copy
- service
- user
- package

## 17. Interview Questions

1. What is an ad-hoc command?
2. What is the difference between command and shell modules?
3. What does -m mean?
4. What does -a mean?
5. What is privilege escalation?
6. How do you install Nginx using Ansible?
7. How do you create a file using Ansible?
