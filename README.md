Role Name: pg_cluster
=========

[![Build Status](https://travis-ci.org/jobcespedes/pg_cluster.svg?branch=master)](https://travis-ci.org/jobcespedes/pg_cluster) [![Buy me a coffee](https://img.shields.io/badge/$-BuyMeACoffee-blue.svg)](https://www.buymeacoffee.com/jobcespedes)

A database cluster using PostgreSQL 11, Pgpool-II 4.0 and Debian 10.

Requirements
------------

- Debian 10
- openssh-server
- netaddr

Role Variables
--------------

- See [`defaults/main.yml`](defaults/main.yml).

Dependencies
------------

- Depends on other Ansible roles: false

Example Playbook
----------------

```yaml
- hosts: all
  roles:
    - jobcespedes.pg_cluster
```

For verifying installation
```yaml
- hosts: all
  tasks:
    - import_role:
        name: jobcespedes.pg_cluster
        tasks_from: verify
```

License
-------

MIT

Author Information
------------------

Job Céspedes Ortiz: jobcespedes@gmail.com
