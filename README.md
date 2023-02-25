| Status | Event |
|---|---|
| [![Code Testing](https://github.com/stevenengland/ntfy_ansible_role/actions/workflows/code_testing.yml/badge.svg?event=schedule)](https://github.com/stevenengland/ntfy_ansible_role/actions/workflows/code_testing.yml) | Weekly schedule |
| [![Code Testing](https://github.com/stevenengland/ntfy_ansible_role/actions/workflows/code_testing.yml/badge.svg?event=pull_request)](https://github.com/stevenengland/ntfy_ansible_role/actions/workflows/code_testing.yml) | Last PR |

Ansible role ntfy
=========

Installs and configures ntfy (server) on linux systems.

Requirements
------------

No special system requirements. `ansible_version_minimum: "4.0.0"` or newer is required.d.

Role Variables
--------------

Here comes a list of variables you can change to meet your requirements. The defaults are listed alongside the variable names.

### Version variables
---
```yaml
ntfy_version: latest
```
Determines which version of ntfy you want to install. Valid values are `latest` or precise versions like `2.0.0`.

### Installation variables
---
```yaml
ntfy_installation_mode: binary
```
There are three possible ways to install ntfy:
* `binary`: Install ntfy by downloading a binary release file.
* `package_download`: Download a platorm specific installation package (.deb, .rpm) for installation. This is supported by operating systems of the Debian and RedHat family.
* `package_repo`: A repo is added to the standard package management toolchain and ntfy is installed from this repo afterwards. This is only supported by operating systems of the Debian family.

---
```yaml
ntfy_installation_mode_binary_systemd_enabled: true
```
Only used when `binary` is the installation mode. 

Choose whether to install a systemd service unit along with the binary.


### Configuration variables
---
```yaml
ntfy_config_mode: dict
```
Choose how you want to configure the ntfy server instance (will be written to `/etc/ntfy/server.yml`). Look at the ntfy server settings documentation for valid values. The ways for configuration are:
* `dict`: A dictionary defined via `ntfy_config_dict` will be used for that.
* `template`: A template will be used that is set via `ntfy_config_template`.

---
```yaml
ntfy_config_dict:
  base-url: "http://localhost"
  cache-file: "{{ ntfy_dirs_cache }}/cache.db"
  attachment-cache-dir: "{{ ntfy_dirs_attachment }}"
```
Build a dictionary that takes the same keys/values that are allowed by the ntfy server configuration.

---
```yaml
ntfy_config_template: None
```
Path to a local template file that will be written to `/etc/ntfy/server.yml`.

### System variables

Hint: The role installs a user/group combination `ntfy`/`ntfy` onto your system. 

---
```yaml
ntfy_system_group_gid: true
```
If you wish you can define a custom gid for the group `ntfy`.

---
```yaml
ntfy_system_user_uid: true
```
If you wish you can define a custom gid for the user `ntfy`.

Dependencies
------------

No dependencies

Example Playbook
----------------

`minimal_runnable_playbook.yml`:

```yaml
# Installs the latest version of ntfy with default values
- hosts: all
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
