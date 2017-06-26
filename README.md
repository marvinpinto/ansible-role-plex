plex
====

[![Build Status](https://img.shields.io/travis/marvinpinto/ansible-role-plex/master.svg?style=flat-square)](https://travis-ci.org/marvinpinto/ansible-role-plex)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-plex-blue.svg?style=flat-square)](https://galaxy.ansible.com/marvinpinto/plex)
[![License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.txt)

Ansible Galaxy role to install and manage [Plex Media Server](https://www.plex.tv/).


Requirements
------------

This role has been tested on Ubuntu 14.04 and will likely only work on an
Ubuntu-like system.


Role Variables
--------------

``` yaml
# Version
plex_server_version: '1.5.7.4016-25d94bad9'

# Application config
#
# Note that if you intend on using these directories, you will need to manually
# point to them from within your plex (GUI) config.
plex_app_transcode_directory: '/opt/plex_transcode'
plex_app_library_directory: '/opt/plex_library'
```


Examples
--------

Install this module from Ansible Galaxy into the './roles' directory:
```bash
ansible-galaxy install marvinpinto.plex -p ./roles
```

Use it in a playbook as follows:
```yaml
- hosts: '127.0.0.1'
  roles:
    - { role: marvinpinto.plex, become: true, tags: ["plex"] }
```

When re-running the playbook to upgrade versions of plex, make the appropriate version update in the `plex_server_version` variable, then you can run only the plex portion of the playbook with `ansible-playbook playbook.yml -t plex`

Development
-----------
Use the supplied `Vagrantfile` for local development and testing (hint: `vagrant up --provision`)
