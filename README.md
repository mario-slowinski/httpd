httpd
=====

Ansible role to configure [httpd server](https://httpd.apache.org/docs/current/).

Requirements
------------

* [ansible.builtin](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)
* [community.general](https://docs.ansible.com/ansible/latest/collections/community/general/)
* [Jinja2](https://jinja.palletsprojects.com/en/2.11.x/)

Role Variables
--------------

* defaults

  ```yaml
  httpd_firewalld: {}     # firewalld settings

  httpd_configs: []       # list of conf.d includes
    - name: "linux"       # name of conf.d include file
      directives: []      # list of Apache config directives
        - oneline: ""     # one line directive, like Alias, starts lowercase
        - Block: ""       # block directive, like Directory, starts uppercase
        - options: []     # list of previous block directive options

  httpd_VirtualHosts: []  # list of VirtualHosts
    - Listen: 80
      Ip: ""              # server IP address to listen on (optional)
      ServerName: ""
      ServerAlias: ""
      DocumentRoot: ""
      directives: []      # list of Apache config directives
        - oneline: ""     # one line directive, like Alias, starts lowercase
        - Block: ""       # block directive, like Directory, starts uppercase
        - options: []     # list of previous block directive options
  ```

* vars

  ```yaml
  httpd_service: ""       # systemd service name

  httpd_pkgs:
    - name: []            # list of httpd server software packages

  httpd_config: {}        # httpd configuration file attributes
  ```

Dependencies
------------

* [service](https://github.com/mario-slowinski/service)
  * [software](https://github.com/mario-slowinski/software)

Tags
----

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
