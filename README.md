# Ansible role that sets up the repositories

[![build status](https://gitlab.com/stiron/ansible-repos/badges/master/build.svg)](https://gitlab.com/stiron/ansible-repos/commits/master)

## Requirements

This module requires Ansible 2.x version.

## Role variables

```
centos_repos:
  epel:
    name: EPEL
    url: "https://dl.fedoraproject.org/pub/epel/{{ ansible_distribution_major_version }}/{{ ansible_architecture }}/"
    gpg_key: "https://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-{{ ansible_distribution_major_version }}" 
    description: EPEL repository

ubuntu_repos:
  ansible:
    url: 'ppa:ansible/ansible'
  docker:
    url: "deb https://apt.dockerproject.org/repo ubuntu-{{ ansible_distribution_release }} main"
    keyserver: hkp://ha.pool.sks-keyservers.net:80
    id: 58118E89F3A912897C070ADBF76221572C52609D
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
