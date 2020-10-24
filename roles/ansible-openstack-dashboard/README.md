<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [ansible-openstack-dashboard](#ansible-openstack-dashboard)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Dependencies](#dependencies)
  - [Example Playbook](#example-playbook)
  - [License](#license)
  - [Author Information](#author-information)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# ansible-openstack-dashboard

An [Ansible](https://www.ansible.com) role to install/configure [OpenStack Dashboard](https://docs.openstack.org/ocata/install-guide-ubuntu/horizon-install.html)

## Requirements

None

## Role Variables

[defaults/main.yml](defaults/main.yml)

## Dependencies

None

## Example Playbook

```yaml
---
- hosts: openstack_controllers
  vars:
  roles:
    - role: ansible-openstack-dashboard
  tasks:
```

## License

MIT

## Author Information

Larry Smith Jr.

-   [EverythingShouldBeVirtual](http://everythingshouldbevirtual.com)
-   [@mrlesmithjr](https://www.twitter.com/mrlesmithjr)
-   <mailto:mrlesmithjr@gmail.com>
