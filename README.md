Role Name
=========

This role allows you to install and setup Elasticsearch.

Requirements
------------

Managed nodes from which tasks will be ran need to have Linux operating systems. Moreover, distributions based on Debian and Red Hat Enterprise Linux (RHEL).

Role Variables
--------------

`defaults/main.yml`

|Variable|Description|
|---|---|
|`elasticsearch_pwd_file`|The file that will contain the password of the `elastic` user. The password should be stored in a vault file after the cluster is started for confidentiality. However, the file itself (without the password) should be kept to prevent the subsequent resetting of the `elastic` user's password.|
|`elasticsearch_major_version`|The major version of Elasticsearch which is used to create package repositories and specify the major version of Elasticsearch to be downloaded.|
|`elasticsearch_minor_version`|The minor version of Elasticsearch used to further specify the version within a major release to download.|
|

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
