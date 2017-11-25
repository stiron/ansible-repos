# Ansible role that sets up the general YUM/APT repositories

[![build status](https://gitlab.com/stiron/ansible-repos/badges/master/build.svg)](https://gitlab.com/stiron/ansible-repos/commits/master)

## Requirements

This module requires **Ansible >2.3** version.

**Root** access is necessary for this role, either run it as `root` or

use `become: true`, otherwise the play will fail.

## Role variables

`centos_repos (dictionary):` Repository configuration for CentOS Linux

`ubuntu_repos (dictionary):` Repository configuration for Ubuntu Linux

The dictionary must look like the following:

```
<system>_repos:
    <repo name>:
        name: <repo name>
        url: <repo or PPA url>
        gpg_key: <gpg key of the repo>
        description: <mandatory description on CentOS>
        keyserver: <keyserver of the repo>
        id: <key id>
        
```

Detailed examples of the role variables:

```
# Adding the EPEL repository on CentOS

centos_repos:
  epel:
    name: EPEL
    url: "https://dl.fedoraproject.org/pub/epel/{{ ansible_distribution_major_version }}/{{ ansible_architecture }}/"
    gpg_key: "https://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-{{ ansible_distribution_major_version }}" 
    description: EPEL repository

# Adding the Ansible and Docker repositories on Ubuntu

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
  vars:
      ubunt_repos:
        ansible:
            url: 'ppa:ansible/ansible'
  roles:
    - repos
```

## Dependencies

None

## License

MIT

## Author

Tamas Molnar - <tmolnar0831@gmail.com>
