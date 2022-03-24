Simple reverse proxy
=========

A role to deploy a simple Nginx reverse proxy in a Docker container.

Requirements
------------

- Docker
- SSL certificate

Role Variables
--------------

For all variables please see `defaults/main.yml`.

    generic_rproxy_issue_domain:
    - decgn-pr-abc.de.valtech.com
    - decgn-pr-xyz.de.valtech.com

Set the list of all domains the certificate should represent. Default is `hostname + .de.valtech.com`

    generic_rproxy_priv_key_path

If you already have a private key to generate Let's Encrypt certificates, you can import your private key by set the path to your key.

Dependencies
------------

None

Example Playbook
----------------

    ---
    - hosts: all
      roles:
        - generic_rproxy_role