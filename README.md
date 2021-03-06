qpid_cpp_server
===============

Ansible role which installs Qpid CPP server.

The configuration of the role is done in such way that it should not be necessary
to change the role for any kind of configuration. All can be done either by
changing role parameters or by declaring completely new configuration as a
variable. That makes this role absolutely universal. See the examples below for
more details.

Please report any issues or send PR.


Examples
--------

```
---

# Example how to use the role
- hosts: myhost1
  roles:
    - qpid_cpp_server

# Example how to change the qpidd setting
- hosts: myhost2
  roles:
    - role: qpid_cpp_server
      qpid_cpp_server_qpidd_config:
        auth: 'no'
```


Role variables
--------------

List of variables used by the role:

```
# Whether to install EPEL YUM repo
qpid_cpp_server_epel_install: "{{ yumrepo_epel_install | default(true) }}"

# EPEL YUM repo URL for RHEL/CentOS 7
qpid_cpp_server_epel_yumrepo_url: "{{ yumrepo_epel_url | default('https://dl.fedoraproject.org/pub/epel/$releasever/$basearch/') }}"

# EPEL YUM repo GPG key
qpid_cpp_server_epel_yumrepo_gpgkey: "{{ yumrepo_epel_gpgkey | default('https://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-$releasever') }}"

# Additional EPEL params
qpid_cpp_server_epel_yumrepo_params: "{{ yumrepo_epel_params | default({}) }}"

# YUM repo for RHEL/CentOS 6 only
qpid_cpp_server_qpid_yumrepo_url: https://copr-be.cloud.fedoraproject.org/results/@qpid/qpid/epel-6-$basearch/

# Additional Qpid YUM repo params
qpid_cpp_server_qpid_yumrepo_params: {}

# Package to be installed (version can be specified here)
qpid_cpp_server_pkg: qpid-cpp-server

# Default storage package (version can be specified here)
qpid_cpp_server_storage_pkg: qpid-cpp-server-linearstore

# Default Qpid daemon config file
qpid_cpp_server_daemon_config_file: /etc/qpid/qpidd.conf

# Default qpidd config
qpid_cpp_server_qpidd_config: {}
```


Dependencies
------------

- [`config_encoder_filters`](https://github.com/jtyr/ansible-config_encoder_filters)


License
-------

MIT


Author
------

Jiri Tyr
