Role Name
=========

An [Ansible] role to configure sysctl settings in order to tweak
network performance more optimally.

Requirements
------------

None

Role Variables
--------------

```
---
# defaults file for ansible-network-tweaks

# Defines if settings should be applied
network_tweaks_enable: true

# Define network tweaks to enable
network_tweaks:
  - name: 'net.ipv4.tcp_tw_reuse'
    value: 1
    set: true
  - name: 'net.ipv4.ip_local_port_range'
    value: "1024 65023"
    set: true
  - name: 'net.ipv4.conf.all.rp_filter'
    # 0 - No source validation
    # 1 - Strict mode as defined in RFC3704 Strict Reverse Path
    #     Each incoming packet is tested against the FIB and if the interface
    #     is not the best reverse path the packet check will fail.
    #     By default failed packets are discarded.
    # 2 - Loose mode as defined in RFC3704 Loose Reverse Path
    #     Each incoming packet's source address is also tested against the FIB
    #     and if the source address is not reachable via any interface
    #     the packet check will fail
    value: 0
    set: false
  - name: 'net.ipv4.conf.default.rp_filter'
    # 0 - No source validation
    # 1 - Strict mode as defined in RFC3704 Strict Reverse Path
    #     Each incoming packet is tested against the FIB and if the interface
    #     is not the best reverse path the packet check will fail.
    #     By default failed packets are discarded.
    # 2 - Loose mode as defined in RFC3704 Loose Reverse Path
    #     Each incoming packet's source address is also tested against the FIB
    #     and if the source address is not reachable via any interface
    #     the packet check will fail
    value: 0
    set: false
  - name: 'net.ipv4.tcp_max_syn_backlog'
    value: 40000
    set: true
  - name: 'net.ipv4.tcp_max_tw_buckets'
    value: 400000
    set: true
  - name: 'net.ipv4.tcp_max_orphans'
    value: 60000
    set: true
  - name: 'net.ipv4.tcp_syncookies'
    value: 1
    set: true
  - name: 'net.ipv4.tcp_synack_retries'
    value: 3
    set: true
  - name: 'net.core.somaxconn'
    value: 40000
    set: true
  - name: 'net.ipv4.tcp_fin_timeout'
    value: 5
    set: true
```

Dependencies
------------

Example Playbook
----------------

```
- hosts: all
  become: true
  vars:
  roles:
    - role: ansible-network-tweaks
  tasks:
```

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com

[Ansible]: <https://www.ansible.com>
