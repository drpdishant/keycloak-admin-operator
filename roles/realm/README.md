Role Name
=========

Ansible Role to manage Keycloak Realm

Requirements
------------

- Running keycloak server
- Keycloak Master admin credentials

Role Variables
--------------

| Variable | Description | Default |
| -- | -- | -- |
| `auth_secret.name` | Secret Name containing admin credentials | - |
| `auth_secret.namespace` | Namespace of Secret containing admin credentials | `default` |
| `auth_client_id` | Keycloak client ID for admin access | `admin-cli` |
| `auth_keycloak_url` | URL of the keycloak server | - |
| `auth_realm` | Realm name to delegate admin access with | `master` |
| `auth_username` | Username for admin auth (overidden if `auth_secret.name` is set) | `admin` |
| `auth_password` | Password for admin auth (not required if `auth_secret.name` is set) | - |
| `realm` | Realm name to create/update | - |
| `validate_certs` | Whether to validate SSL certificates or not | `true` |

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set
for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for
users too:

```yaml
---
- hosts: localhost
  connection: local
  vars:
    auth_secret:
      name: "example-kc-initial-admin" #"{{ ansible_operator_meta.name }}-secret"
      namespace: "default" #"{{ansible_operator_meta.namespace }}"
    auth_keycloak_url: "https://kc.korifi.run"
    auth_client_id: "admin-cli"
    auth_realm: master
    realm: demo
  roles:
  - roles/realm
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
