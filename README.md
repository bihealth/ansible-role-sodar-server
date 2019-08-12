[![Build Status](https://travis-ci.org/bihealth/ansible-role-sodar-server.svg?branch=master)](https://travis-ci.org/bihealth/ansible-role-sodar-server)

# SODAR Server

Setup of SODAR Server.

## Requirements

- A PostgreSQL server has to be setup independently (cf. `bihealth.postgres_server`).
- A SODAR Taskflow instance has to be setup as well (cf. `bihealth.sodar_taskflow`).
- iRODS and Davrods have to be setup independently (cf. `bihealth.irods_server` and `bihealth.davrods`).

## Role Variables

See `defaults/main.yml` for all role variables and their documentation.

## Dependencies

- `bihealth.sodar_core_app`

## Example Playbook

```yaml
- hosts: servers
  vars:
    # bihealth.sodar_core_app ---------------------------------------------------------------------
    sodar_core_app_version: "v0.1.0"
    sodar_core_app_django_secret_key: "SOMESECRETKEYSOMESECRETKEYSOMESECRETKEYSOMESECRETKEY"
    sodar_core_app_superuser_password: "junkpass"
    # bihealth.ssl_certs --------------------------------------------------------------------------
    ssl_certs_certs:
      - name: sodar.example.com
    # bihealth.postgres_client --------------------------------------------------------------------
    postgres_client_host: 127.0.0.1
    postgres_client_db: sodar-test
    postgres_client_user: sodar-test
    postgres_client_password: sodar-test
  roles:
    - role: bihealth.sodar_server
```

## Open Issue

- Use Travis CI with Ansible Molecule for testing deployment once SODAR is published.

## License

MIT

## Author Information

- Manuel Holtgrewe

Created with love at [Core Unit Bioinformatics (CUBI), Berlin Institute of Health (BIH)](https://www.cubi.bihealth.org).
