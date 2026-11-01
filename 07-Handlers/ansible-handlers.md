# Ansible Handlers

## 1. What is a Handler?

A handler is a special task that runs when another task notifies it.

Handlers are commonly used to restart or reload services after configuration changes.

## 2. Why Use Handlers?

Imagine you update the Nginx configuration file.

You only need to restart Nginx if the configuration actually changes.

A handler helps automate this.

## 3. Example

    ---
    - name: Configure Nginx
      hosts: all
      become: true

      tasks:
        - name: Install nginx
          apt:
            name: nginx
            state: present

        - name: Update nginx configuration
          copy:
            src: nginx.conf
            dest: /etc/nginx/nginx.conf
          notify: Restart nginx

      handlers:
        - name: Restart nginx
          service:
            name: nginx
            state: restarted

## 4. Important Keywords

### notify
Triggers a handler when a task reports a change.

### handlers
Defines special tasks that are triggered by notifications.

### listen
Allows handlers to listen to a named notification topic.

## 5. Important Handler Behaviour

- Handlers run only when notified.
- Handlers normally execute once per play, even if notified multiple times.
- Handlers normally run after regular tasks.
- A task that does not report a change does not trigger its handler.

## 6. Interview Questions

1. What is a handler?
2. What is notify?
3. When does a handler execute?
4. Can a handler execute multiple times in one play?
5. What is the difference between a task and a handler?
