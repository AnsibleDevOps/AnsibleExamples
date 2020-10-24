Role Name
=========

Installs and configured Elastic topbeat (https://www.elastic.co/products/beats/topbeat)

Requirements
------------

None

Vagrant
-------
Spin up and test  
Spins up 3 nodes to test with following:  
topbeat  - client  
es  - elasticsearch  
logstash  - logstash server  
````
vagrant up
````

Role Variables
--------------

````
---
# defaults file for ansible-es-topbeat
es_topbeat_dashboard_dir: '/opt/beats-dashboards-{{ es_topbeat_version }}'
es_topbeat_dashboard_dl: 'http://download.elastic.co/beats/dashboards/{{ es_topbeat_dashboard_package }}'
es_topbeat_dashboard_package: 'beats-dashboards-{{ es_topbeat_version }}.zip'
es_topbeat_debian_package: 'topbeat_{{ es_topbeat_version }}_amd64.deb'
es_topbeat_dl_url: 'https://download.elastic.co/beats/topbeat'
es_topbeat_elasticsearch_host: 'es.{{ pri_domain_name }}:9200'
es_topbeat_input:
  period: 10
  procs: '.*'
  stats:
    system: true
    proc: true
    filesystem: true
    cpu_per_core: false
es_topbeat_outputs:
  - name: elasticsearch
    host: '{{ es_topbeat_elasticsearch_host }}'
    workers: 1
es_topbeat_redhat_package: 'topbeat-{{ es_topbeat_version }}-x86_64.rpm'
es_topbeat_version: '1.2.3'
pri_domain_name: 'example.org'
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
    - role: ansible-es-topbeat
  tasks:
````
#### Galaxy
````
- hosts: all
  become: true
  vars:
  roles:
    - role: mrlesmithjr.topbeat
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
