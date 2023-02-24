Ansible role ntfy
=========

Installs and configures ntfy (server) on linux systems.

Requirements
------------

No special system requirements. `ansible_version_minimum: "4.0.0"` or newer is required.d.

Role Variables
--------------

TBD

Dependencies
------------

No dependencies

Example Playbook
----------------

`minimal_runnable_playbook.yml`:

```
# Installs the latest version of ntfy with default values
- hosts: all
    become: yes
    roles:
        - { role: stevenengland.ntfy }
```

Contributing
-------

We encourage you to contribute to this role! Please check out the
[contributing guide](CONTRIBUTE.md) for guidelines about how to proceed.

License
-------

MIT
