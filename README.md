# Simple reverse proxy

A role to deploy a simple Nginx reverse proxy for SSL/TLS termination in a Docker container.
This role is designed to work together with the ACME role from https://github.com/ValtechMobility/generic_acme_role.

## Requirements

- Docker
- SSL certificate

## Role Variables

For all variables please see `defaults/main.yml`.

### Mandatory

    generic_rproxy_domain: "example.com"

Domain of the reverse proxy. Needs to be the same name

    generic_rproxy_redirects:
      "/": "http://example.org/"
      "/net": "http://example.net/"

Directory of redirects. If you want to link containers then use the container name as URL.

    generic_rproxy_container_links:
    - jenkins

List of linked containers. This is only necessary if you want to use the container names in the redirects.

## Example Playbook

    ---
    - hosts: all
      roles:
        - generic_rproxy_role
      vars:
        generic_rproxy_domain: "example.com"
        generic_rproxy_redirects:
          "/": "http://example.org/"
          "/net": "http://example.net/"

[examples/deploy-rproxy.yml](examples/deploy-rproxy.yml)

    ---
    - hosts: all
      roles:
        - generic_rproxy_role
      vars:
        generic_rproxy_domain: "example.com"
        generic_rproxy_redirects:
          "/": "http://jenkins:8080/"
        generic_rproxy_container_links:
        - jenkins

[examples/deploy-rproxy-container.yml](examples/deploy-rproxy-container.yml)