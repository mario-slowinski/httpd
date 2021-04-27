httpd
=====

Ansible role to configure httpd server.

Requirements
------------

* [ansible.builtin](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)
* [community.general](https://docs.ansible.com/ansible/latest/collections/community/general/)

Role Variables
--------------

* defaults

  ```yaml
  httpd_firewalld: {}         # firewalld settings

  httpd_VirtualHosts: []      # list of VirtualHosts
    - ServerName: ""
      Listen: 80
      ServerAlias: ""
      DocumentRoot: ""
  ```

* vars

  ```yaml
  httpd_pkgs:
    - name: []                # list of httpd server software packages
  ```

Dependencies
------------

* [service](https://github.com/mario-slowinski/service)
  * [software](https://github.com/mario-slowinski/software)

Tags

* httpd.config
  * httpd.config.vhost
  * httpd.config.port
* httpd.selinux

Example Playbook
----------------

* `requirements.yml`

  ```yaml
  - name: httpd
    src: https://github.com/mario-slowinski/httpd
  ```

* playbook usage

  ```yaml
  - hosts: servers
    gather_facts: true  # to get ansible_os_family
    roles:
      - role: httpd
  ```

License
-------

[GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.html)

Author Information
------------------

[mario.slowinski@gmail.com](mailto:mario.slowinski@gmail.com)
