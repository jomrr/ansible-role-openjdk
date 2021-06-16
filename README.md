# ansible-role-openjdk

![GitHub](https://img.shields.io/github/license/jam82/ansible-role-openjdk) ![GitHub last commit](https://img.shields.io/github/last-commit/jam82/ansible-role-openjdk) ![GitHub issues](https://img.shields.io/github/issues-raw/jam82/ansible-role-openjdk) ![Travis (.com) branch](https://img.shields.io/travis/com/jam82/ansible-role-openjdk/main?label=travis) [![Molecule](https://github.com/jam82/ansible-role-openjdk/actions/workflows/molecule.yml/badge.svg)](https://github.com/jam82/ansible-role-openjdk/actions/workflows/molecule.yml)

**Ansible role for installing openjdk.**

## Supported Platforms

| OS Family | Distribution  | Latest | Supported Version(s) | Comment |
|-----------|---------------|--------|----------------------|---------|
| Alpine    | Alpine        | :heavy_check_mark: | 3.12, 3.13 | |
| Archlinux | Archlinux     | :heavy_check_mark: | - | |
|           | Manjaro       | :heavy_check_mark: | - | |
| Debian    | Debian        | :heavy_check_mark: | 10, 11 | |
|           | Ubuntu        | :heavy_check_mark: | 18.04, 20.04 | |
| RedHat    | Almalinux     | :heavy_check_mark: | 7, 8 | |
|           | Amazonlinux   | :x: | - | not tested, image not working |
|           | Centos        | :heavy_check_mark: | 8 | |
|           | Fedora        | :heavy_check_mark: | 33, 34, Rawhide | |
|           | Oraclelinux   | :heavy_check_mark: | 7, 8 | |
| Suse      | OpenSuse Leap | :heavy_check_mark: | 15.1, 15.2, 15.3 | |
|           | Tumbleweed    | :heavy_check_mark: | - | |

## Requirements

Ansible 2.9 or higher.

## Variables

Variables and defaults for this role.

### defaults/main.yml

```yaml
openjdk_role_enabled: false
```

## Dependencies

None.

## Example Playbook

```yaml
---
# role: ansible-role-openjdk
# play: openjdk
# file: openjdk.yml

- hosts: all
  become: true
  gather_facts: true
  vars:
    openjdk_role_enabled: true
  roles:
    - role: ansible-role-openjdk
```

## License and Author

- Author:: [jam82](https://github.com/jam82/)
- Copyright:: 2021, [jam82](https://github.com/jam82/)

Licensed under [MIT License](https://opensource.org/licenses/MIT).
See [LICENSE](https://github.com/jam82/ansible-role-openjdk/blob/master/LICENSE) file in repository.

## References

- [ArchWiki](https://wiki.archlinux.org/)
