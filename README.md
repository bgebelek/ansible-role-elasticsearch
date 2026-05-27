Elasticsearch
=============

This role installs and configures Elasticsearch on managed nodes via the [Elastic APT](https://www.elastic.co/docs/deploy-manage/deploy/self-managed/install-elasticsearch-with-debian-package) or [RPM](https://www.elastic.co/docs/deploy-manage/deploy/self-managed/install-elasticsearch-with-rpm) repository depending on the OS family of the managed node.

Requirements
------------

Managed nodes must be running a Linux distribution from either the Debian or RedHat family.

Role Variables
--------------

`defaults/main.yml`

| Variable | Description |
|---|---|
| `elasticsearch_major_version` | The major version of Elasticsearch to install (e.g. `9`). Determines the repository URL used for both DEB and RPM package sources. |
| `elasticsearch_minor_version` | The minor and patch version of Elasticsearch to install (e.g. `2.1`). Combined with `elasticsearch_major_version` to pin the installed package to a specific version. |
| `elasticsearch_pwd_file` | The name of the file used to store the elastic user password. On the first run, the role resets and stores the password in this file automatically. For subsequent runs, the password should be assigned to the variable `elastic_password`. This file should be kept empty and in-place to prevent future resetting of the elastic user's password. |
| `elasticsearch_pwd_path` | The directory where the elastic user password file is stored. This variable has no meaningful default and must be set by the user. |

Required Variables
------------------

These variables can be configured in `group_vars`, `host_vars`, or inventory files depending on the desired precedence.

| Variable | Description |
|---|---|
| `elastic_password` | The elastic user password. On subsequent runs, the role expects this variable to be provided via an Ansible Vault encrypted file. |

Dependencies
------------

This role has no dependencies on other roles in Ansible Galaxy. However, it is intended to be used alongside the `bgebelek.kibana` role, which configures a Kibana instance to connect to the Elasticsearch node this role provisions.

Example Playbook
----------------

```yaml
---

- name: Install Elasticsearch
  hosts: linux_servers
  roles:
    - bgebelek.elasticsearch
```

License
-------

GPL-3.0-only

Author Information
------------------

Please open issues in the remote repository https://github.com/bgebelek/ansible-role-elasticsearch/issues for any problems encountered while using this role.
