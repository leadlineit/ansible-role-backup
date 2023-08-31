# Ansible Galaxy role for create backup scripts for locale backups.

![Build Status](https://github.com/leadlineit/ansible-role-backup/actions/workflows/ansible-galaxy-ci.yml/badge.svg)
[![Galaxy Role](https://img.shields.io/badge/Ansible--Galaxy-leadlineit.backup-blue.svg?logo=ansible&logoColor=white)](https://galaxy.ansible.com/leadlineit/backup/)

This role helps to create backup scripts for locale backups.

Supported OSes
--------------
- Debian 12 (bookworm)
- Debian 11 (bullseye)
- Debian 10 (buster)
- Debian 9 (stretch)

Requirements
------------

This role requires Ansible 2.11 or higher.

Role Variables
--------------

```yaml
---
backup:
  - name: etc
    script: backup_etc.sh
    backup_parent_dir: /data/bkp_test/
  - name: mysql
    script: backup_mysql.sh
    retention: 14
    backup_parent_dir: /some_bkp_dir/bases/
  - name: pgsql
    script: backup_pgsql.sh
    retention: 14
  - name: sites
    script: backup_sites.sh
  - name: homes
    script: backup_homes.sh

```

A "retention" and "backup_parent_dir" variables optional.
Default value for "retention" (in days) and for "backup_parent_dir":

```yaml
---
backup:
  - name: some-script
    retention: 14
    backup_parent_dir: /data/backups/{{name-of-script}}
```
Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
    - { role: leadlineit.backup, tags: backup }
```

License
-------

BSD

Author Information
------------------

This role was created by Stas Stavnichuk.
