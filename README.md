docker-media-converter
======================

[![Build Status](https://img.shields.io/travis/marvinpinto/ansible-role-docker-media-converter/master.svg?style=flat-square)](https://travis-ci.org/marvinpinto/ansible-role-docker-media-converter)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-docker--media--converter-blue.svg?style=flat-square)](https://galaxy.ansible.com/marvinpinto/docker-media-converter)
[![License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.txt)

Ansible Galaxy role to manage and run a
[media-converter](https://github.com/marvinpinto/docker-media-converter) docker
container.


Requirements
------------

This role has been tested on Ubuntu 14.04 and will likely only work on an
Ubuntu-like system. You will also need a functioning docker environment and a
recent-is version of `docker-py` for this role to work.

If you have neither and would like ansible to set this up for you, have a look
at the [marvinpinto.docker](https://galaxy.ansible.com/marvinpinto/docker)
Galaxy role.


Role Variables
--------------

```yaml
# Docker container name
docker_media_converter_container_name: 'mediaconverter'

# Media directories that need to be mounted inside the container
docker_media_container_exposed_volumes: []

# Container environment variables
docker_media_container_env_variables: {}
```


Examples
--------

Install this module from Ansible Galaxy into the './roles' directory:
```bash
ansible-galaxy install marvinpinto.docker-media-converter -p ./roles
```

Use it in a playbook as follows:
```yaml
- hosts: '127.0.0.1'
  roles:
    - role: 'marvinpinto.docker-media-converter'
      become: true
      docker_media_container_env_variables:
        MEDIA_TVSHOWS: '/tv'
        MEDIA_MOVIES: '/movies'
        PLEX_URL: 'http://127.0.0.1:32400'
        PLEX_TOKEN: 'sekr3t'
      docker_media_container_exposed_volumes:
        - '/opt/data/tv:/tv'
        - '/opt/data/movies:/movies'
```
