Role Name
=========

flink: Flink

[![Build Status](https://travis-ci.org/cmihai-ansible/flink.svg?branch=master)](https://travis-ci.org/cmihai-ansible/flink)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.flink](https://galaxy.ansible.com/devopstoolbox.flink)

```bash
ansible-galaxy install devopstoolbox.flink
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
flink_packages_state: present
flink_remove_packages: true
flink_enable_service: true
flink_enable_selinux: true
flink_copy_templates: true
flink_firewall_configure: true
flink_firewall_rules:
  - service: ssh
  - port: 3389
flink_users:
  - user: devops
    group: docker
flink_selinux_booleans:
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
- name: Install flink on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: flink is configured
      import_role:
        name: devopstoolbox.flink
      vars:
        flink_packages_state: present
        flink_remove_packages: true
        flink_enable_service: true
        flink_enable_selinux: true
        flink_copy_templates: true
        flink_firewall_configure: true
        flink_firewall_rules:
          - service: ssh
          - port: 3389
        flink_users:
          - user: devops
            group: docker
        flink_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: flink
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
