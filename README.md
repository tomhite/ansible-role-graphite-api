Stouts.graphite-api
==============

[![Build Status](http://img.shields.io/travis/Stouts/Stouts.graphite-api.svg?style=flat-square)](https://travis-ci.org/Stouts/Stouts.graphite-api)
[![Galaxy](http://img.shields.io/badge/galaxy-Stouts.graphite-api-blue.svg?style=flat-square)](https://galaxy.graphite-api.com/list#/roles/1944)
[![Tag](http://img.shields.io/github/tag/Stouts/Stouts.graphite-api.svg?style=flat-square)]()

Ansible role which manage [Graphite-API](http://graphite-api.readthedocs.org/en/latest/)

* Install and configure Graphite-Api
* Install and configure Graphite-Carbon and Graphite-Whisper


#### Variables

Here is the list of all variables and their default values:

```yaml
graphite_api_enabled: yes                     # The role is enabled

graphite_api_home: /srv/graphite              # Installation directory
graphite_api_user: graphite                   # Set owner
graphite_api_group: "{{ graphite_api_user }}" # Set group

# Setup Graphite-API
graphite_api_timezone: Europe/Berlin
graphite_api_whisper_directories:
- "{{graphite_api_home}}/storage/whisper"
graphite_api_search_index: "{{graphite_api_home}}/index"

# Setup Graphite-Carbon
graphite_api_carbon: yes                    # Install and setup Graphite Carbon

# Setup Graphite-Whisper
graphite_api_whisper: yes

# Setup storage schemas
graphite_api_storage_schemas:
- name: stats
  priority: 110
  pattern: ^stats\..*
  retentions: "10s:6h,1m:7d,10m:1y"
- name: carbon
  pattern: ^carbon\.
  retentions: "60:90d"
- name: default
  pattern: ".*"
  retentions: "60s:1d"

# Setup Gunicorn
graphite_api_gunicorn_host: 127.0.0.1
graphite_api_gunicorn_port: 8080

# Setup NGINX
graphite_api_nginx_host: "{{inventory_hostname}}"
graphite_api_nginx_port: 80
graphite_api_nginx_allow_origin: yes

# The following parameters are for toggling dependencies
nginx_enabled: yes
python_enabled: yes
```

#### Usage

Add `Stouts.graphite-api` to your roles and setup the variables in your playbook file.
Example:

```yaml

- hosts: all

  roles:
    - Stouts.graphite-api

  vars:
    graphite_api_nginx_port: 8888
```

#### License

Licensed under the MIT License. See the LICENSE file for details.

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Stouts/Stouts.graphite-api/issues)!
