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

Role Variables
--------------

````
---
# defaults file for ansible-observium
observium_admin_account_info:
  email: 'observium@{{ pri_domain_name }}'
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
  - fping
  - graphviz
  - imagemagick
  - ipmitool
  - libapache2-mod-php5
  - mtr-tiny
  - mysql-client
  - php-pear
  - php5-cli
  - php5-gd
  - php5-json
  - php5-mcrypt
  - php5-mysql
  - python-mysqldb
  - rrdtool
  - snmp
  - subversion
  - whois
#  - mysql-server
observium_dl_dir: '/opt'
observium_dl_package: 'observium-community-latest.tar.gz'
observium_dl_url: 'http://www.observium.org'
observium_monitor_libvirt_vms: false  #Define if desired to monitor LibVirt VM's
pri_domain_name: 'vagrant.local'
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
