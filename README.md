# Ansible role that sets up the repositories
[![build status](https://gitlab.com/stiron/ansible-repos/badges/master/build.svg)](https://gitlab.com/stiron/ansible-repos/commits/master)

## Requirements

This module requires Ansible 2.x version.

## Role variables

```
centos_repos:
  epel:
    name: EPEL
    url: "https://dl.fedoraproject.org/pub/epel/epel-release-latest-{{ ansible_distribution_major_version }}.noarch.rpm"
    gpg_key: "https://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-{{ ansible_distribution_major_version }}"
    description: EPEL repository

ubuntu_repos:
  ansible:
    name: ansible
    url: 'ppa:ansible/ansible'
```

## Examples

```
- hosts: all 
  roles:
    - repos
```

## Dependencies

None

## License

BSD

## Author

Tamas Molnar
