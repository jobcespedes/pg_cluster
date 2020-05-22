Role Name: pg_cluster
=========

[![Build Status](https://travis-ci.org/jobcespedes/pg_cluster.svg?branch=master)](https://travis-ci.org/jobcespedes/pg_cluster) [![Buy me a coffee](https://img.shields.io/badge/$-BuyMeACoffee-blue.svg)](https://www.buymeacoffee.com/jobcespedes)

A database cluster using Postgres (11), Pgpool2 (4.0) and Debian (10).

The cluster has 3 nodes. Each node runs Pgpool2 and Postgres. Pgpool2 and Postgres have two roles each. For Postgres, those roles are: primary and standby. For Pgpool2, those roles are: active and stanby. Pgpool and Postgres roles are independent. However, the first node starts with both, active (pgpool2) and primary(postgres). It has a Floating IP. The rest of nodes have standby role (pgpool and postgres).
```Plaintext
                  FLOATING IP
                 +-----------+     WATCHDOG
        +--------|  PGPOOL2  |--------+
        |        ------------- nic0   |
        |        |           |        |
        |        | POSTGRES  |        |
        |        | master    |        |
        |        +-----------+        |
        |          nic1|              |
  +-----------+        |        +-----------+
  |  PGPOOL2  |        |        |  PGPOOL2  |
  |-----------|        |        -------------
  |           |        |        |           |
  | POSTGRES  |        |        | POSTGRES  |
  | standby   |-----------------| stanby    |
  +-----------+   REPLICATION   +-----------+
```

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
