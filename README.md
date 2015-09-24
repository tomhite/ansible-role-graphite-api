# Ansible Role: Apache 2.x

An Ansible Role that deploys a docker container running the graphite-api server and graphite carbon cache listener.

## Requirements

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    graphite_api_enabled: yes 

Flag indicating whether to install the docker container 

    graphite_api_build_docker: yes

Flag indicating whether to rebuild the image from the Dockerfile

    graphite_api_dockerfile_path: ../../../../containers/docker/graphite-api/
    graphite_api_container_build_dir: /var/lib/container/graphite-api

Temporary variables indicating locations for fine the Dockerfile and supporting files, and where to located them on the host(s) for the build process 

    graphite_api_gunicorn_port: 8080

Port on which the graphite-api interface is exposed

    graphite_api_carbon_udp_port: 2003

Port for the carbon cache metrics listener

## Dependencies

## Example Playbook

## License

## Author Information

