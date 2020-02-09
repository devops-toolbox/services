Role Name
=========

services: Services

[![Build Status](https://travis-ci.org/cmihai-ansible/services.svg?branch=master)](https://travis-ci.org/cmihai-ansible/services)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.services](https://galaxy.ansible.com/devopstoolbox.services)

```bash
ansible-galaxy install devopstoolbox.services
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
services_packages_state: present
services_remove_packages: true
services_enable_service: true
services_enable_selinux: true
services_copy_templates: true
services_firewall_configure: true
services_firewall_rules:
  - service: ssh
  - port: 3389
services_users:
  - user: devops
    group: docker
services_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install services on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: services is configured
      import_role:
        name: devopstoolbox.services
      vars:
        services_packages_state: present
        services_remove_packages: true
        services_enable_service: true
        services_enable_selinux: true
        services_copy_templates: true
        services_firewall_configure: true
        services_firewall_rules:
          - service: ssh
          - port: 3389
        services_users:
          - user: devops
            group: docker
        services_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: services
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
