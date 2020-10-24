Role Name
=========

Installs rancid (Really Awesome New Cisco confIg Differ) http://www.shrubbery.net/rancid/
#####Configurable (Git enabled)

Requirements
------------

Any devices to back up will need an account defined for rancid to connect to and perform backups.

Role Variables
--------------

````
email_notifications:  #defined in group_vars/all/configs or define here
pri_domain_name: example.org #defines primary domain name...define here or globally in group_vars/all
rancid_base_dir: /opt/rancid
rancid_config_devices: true
rancid_config_remote: true  #only enable this for true after adding rancid ssh keys to git remote repo
rancid_cron:
  schedule:
    minute: 0
    hour: '*/12'
rancid_devices:
  - name: 'switch01.{{ pri_domain_name }}'
    groups:
      - switches
    type: cisco
    state: up
rancid_git_email: '{{ rancid_git_user }}@{{ pri_domain_name }}'
rancid_git_remote: 'git@{{ rancid_git_server }}:rancid/rancid.git'
rancid_git_server: 'gitlab.{{ pri_domain_name }}'
rancid_git_user: '{{ rancid_user }}'
rancid_groups:
  - firewalls
  - routers
  - switches
  - test
rancid_groups_email:
  - name: firewalls
    email:
      - name: '{{ email_notifications }}'
  - name: routers
    email:
      - name: '{{ email_notifications }}'
  - name: switches
    email:
      - name: '{{ email_notifications }}'
  - name: test
    email:
      - name: '{{ email_notifications }}'
rancid_home_dir: '{{ rancid_base_dir }}'
rancid_html_email: true
rancid_locktime: 4
rancid_login_enable_password:  #defined in group_vars/all/accounts or define here...enable password for devices
rancid_login_password:  #defined in group_vars/all/accounts or define here...login password for rancid user on devices
rancid_max_rounds: 3
rancid_rcs: git
rancid_repo: https://github.com/dotwaffle/rancid-git
rancid_simultaneous_count: 10
rancid_source_dir: '{{ rancid_base_dir }}/src'
rancid_tmp_dir: /tmp
rancid_user: rancid
rancid_user_email: '{{ rancid_user }}@{{ pri_domain_name }}'
rancid_web_group: www-data
````

Dependencies
------------

None

Example Playbook
----------------

#### GitHub
````
- hosts: all
  become: true
  vars:
  roles:
    - role: ansible-rancid-git
  tasks:
````

#### Galaxy
````
- hosts: all
  become: true
  vars:
  roles:
    - role: mrlesmithjr.rancid-git
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
