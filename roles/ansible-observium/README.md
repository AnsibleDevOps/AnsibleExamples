Role Name
=========

An Ansible role to install/configure Observium Monitoring....
http://www.observium.org/

Requirements
------------

Install required Ansible roles...
````
ansible-galaxy install -r requirements.yml
````

Vagrant
-------
Easily spin up a Vagrant Lab...
````
cd vagrant
vagrant up
````
Open your browser to http://127.0.0.1:8080
And login
````
user: admin
password: observium
````
When you are all done and ready to clean-up the Vagrant Lab...
````
./cleanup.sh
````

Role Variables
--------------

````
---
# defaults file for ansible-observium
observium_admin_account_info:
  email: 'observium@{{ pri_domain_name }}'
  email_to: 'root@localhost'
  email_default_only: 'TRUE'
  level: 10
  password: 'observium'
  username: 'admin'
observium_base_dir: '{{ observium_dl_dir }}/observium'
observium_db_info:
  db: 'observium'
  host: '127.0.0.1'
  password: 'observium'
  user: 'observium'
observium_debian_pre_reqs:
  - apache2
  - fping
  - graphviz
  - imagemagick
  - ipmitool
  - libapache2-mod-php7.2
  - mtr-tiny
  - mysql-server
  - mysql-client
  - php-pear
  - php7.2-cli
  - php7.2-gd
  - php7.2-json
  - php7.2-mysql
  - php7.2-mysqli
  - python-mysqldb
  - rrdtool
  - snmp
  - subversion
  - whois
  - snmp-mibs-downloader

observium_dl_dir: '/opt'
observium_dl_package: 'observium-community-latest.tar.gz'
observium_dl_url: 'http://www.observium.org'
observium_monitor_libvirt_vms: false  #Define if desired to monitor LibVirt VM's
pri_domain_name: 'vagrant.local'
observium_snmp_community_list:   # define a list of default communities to try when adding devices
  - '"public"'    # requires that the quotes are inside single quotation marks to keep the quotes in the config.php

# If we wish to use the paid for version this will allow us to use
observium_commercial: false                                                                     # Do we wish to use opensource version
observium_commercial_svn_user: ""                                                               # SVN user for commercial version
observium_commercial_svn_password: ""                                                           # SVN password for commercial version
observium_commercial_svn_repo: "http://svn.observium.org/svn/observium/branches/stable"         # Repo to pull commercial version from
````

Dependencies
------------

Install required Ansible roles from Requirements section.

Example Playbook
----------------

````
- hosts: all
  become: true
  vars:
    - pri_domain_name: 'test.vagrant.local'
  roles:
    - role: ansible-apache2
    - role: ansible-mariadb-mysql
    - role: ansible-observium
  tasks:
````

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
