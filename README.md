Role Name
=========

tomcat: Tomcat

[![Build Status](https://travis-ci.org/cmihai-ansible/tomcat.svg?branch=master)](https://travis-ci.org/cmihai-ansible/tomcat)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.tomcat](https://galaxy.ansible.com/devops-toolbox.tomcat)

```bash
ansible-galaxy install devops-toolbox.tomcat
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
tomcat_packages_state: present
tomcat_remove_packages: true
tomcat_enable_service: true
tomcat_enable_selinux: true
tomcat_copy_templates: true
tomcat_firewall_configure: true
tomcat_firewall_rules:
  - service: ssh
  - port: 3389
tomcat_users:
  - user: devops
    group: docker
tomcat_selinux_booleans:
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
- name: Install tomcat on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: tomcat is configured
      import_role:
        name: devops-toolbox.tomcat
      vars:
        tomcat_packages_state: present
        tomcat_remove_packages: true
        tomcat_enable_service: true
        tomcat_enable_selinux: true
        tomcat_copy_templates: true
        tomcat_firewall_configure: true
        tomcat_firewall_rules:
          - service: ssh
          - port: 3389
        tomcat_users:
          - user: devops
            group: docker
        tomcat_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: tomcat
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
