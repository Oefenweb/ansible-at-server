## at-server

[![CI](https://github.com/Oefenweb/ansible-at-server/workflows/CI/badge.svg)](https://github.com/Oefenweb/ansible-at-server/actions?query=workflow%3ACI)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-at--server-blue.svg)](https://galaxy.ansible.com/Oefenweb/at-server/)

Set up a persistent channel for queuing commands (using `at`) in Debian-like systems (server side).

#### Requirements

* `at` (will be installed)
* `openssh-server` (will not be installed)
* `bash` (will not be installed)

#### Variables

* `at_server_user`: [default: `at`]: The user that will accept the `at` connection
* `at_server_group`: [default: `at`]: The primary group of the `at` user
* `at_server_groups`: [default: `['ssh_users']`]: The secondary groups of the `at` user
* `at_server_shell`: [default: `/bin/bash`]: The shell of the `at` user

* `at_server_authorized_keys`: [default: `[]`]: Authorized key declarations
* `at_server_authorized_keys.{n}.src`: [required]: The local path of the key
* `at_server_authorized_keys.{n}.state`: [optional, default: `present`]: State

## Dependencies

None

## Recommended

* `ansible-ssh-server` ([see](https://github.com/Oefenweb/ansible-ssh-server))
* `ansible-at-client` ([see](https://github.com/Oefenweb/ansible-at-client))

#### Example

```yaml
---
- hosts: all
  roles:
    - at-server
  vars:
    at_server_groups:
      - ssh_users
    at_server_authorized_keys:
      - src: ../../../files/at/home/at/.ssh/id_rsa.pub
```

#### License

MIT

#### Author Information

Mischa ter Smitten

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Oefenweb/ansible-at-server/issues)!
