Elasticsearch
=========

This role allows you to install and setup Elasticsearch.

Requirements
------------

Managed nodes where these tasks will be ran need to have Linux operating systems. Moreover, distributions based on Debian and Red Hat Enterprise Linux (RHEL).

Role Variables
--------------

`defaults/main.yml`

|Variable|Description|
|---|---|
|`elasticsearch_pwd_file`|The file that will contain the password of the `elastic` user. The password should be stored in a vault file after the cluster is started for confidentiality. However, the file itself (without the password) should be kept to prevent the subsequent resetting of the `elastic` user's password.|
|`elasticsearch_pwd_path`|The absolute path to the file above. The placeholder value for this variable should be replaced before using this role.|
|`elasticsearch_major_version`|The major version of Elasticsearch which is used to create package repositories and specify the major version of Elasticsearch to be downloaded.|
|`elasticsearch_minor_version`|The minor version of Elasticsearch used to further specify the version within a major release to download.|

Required Variables
------------

|Variable|Description|
|---|---|
|`elastic_password`|The password for the `elastic` user. This should be kept in a vault file after the cluster is first setup.|

Dependencies
------------

Although this role will work by itself, it is intended to be used with the role `bgebelek.kibana`. If used with `bgebelek.kibana`, this role should run first.

Example Playbook
----------------

```yaml
---

- name: Manage Elasticsearch
  hosts:
    - linux_servers
  roles:
    - bgebelek.elasticsearch
```

License
-------

GPL-3.0-only

Author Information
------------------

Please open issues in the remote repository https://github.com/bgebelek/ansible-role-elasticsearch for any problems encountered while using this role.
