# Ansible Role: openjdk

![GitHub](https://img.shields.io/github/license/jomrr/ansible-role-openjdk)
![GitHub last commit](https://img.shields.io/github/last-commit/jomrr/ansible-role-openjdk)
![GitHub issues](https://img.shields.io/github/issues-raw/jomrr/ansible-role-openjdk)
[![dev](https://img.shields.io/github/actions/workflow/status/jomrr/ansible-role-openjdk/dev.yml?branch=dev&event=push&label=dev)](https://github.com/jomrr/ansible-role-openjdk/actions/workflows/dev.yml?query=branch%3Adev)
[![main](https://img.shields.io/github/actions/workflow/status/jomrr/ansible-role-openjdk/main.yml?branch=main&event=push&label=main)](https://github.com/jomrr/ansible-role-openjdk/actions/workflows/main.yml?query=branch%3Amain)

Install the selected OpenJDK development kit or runtime from distribution
packages.

## Purpose

Ensures that distribution packages for the selected OpenJDK major version and
development kit or runtime are installed. Installation is idempotent: subsequent
runs with the same inputs leave installed packages unchanged.

## Scope

### Managed

- OpenJDK development kit or runtime packages for the selected major version.
- Headless JRE packages and, on Debian-based systems, headless JDK packages.

### Not Managed

- Selection of the active Java version when multiple versions are installed.
- JAVA_HOME, application configuration, and removal of previously installed Java
  packages.

## Dependencies

```yaml
collections:
  - name: community.general
    version: '>=12.0.0'
```

## Role Variables

### `openjdk_type`

Type: `str`. Required: `false`.

Install the development kit, including the Java compiler, or only the Java
runtime.

Default:

```yaml
openjdk_type: jdk
```

### `openjdk_headless`

Type: `bool`. Required: `false`.

Select headless packages where the platform provides a matching variant.
Applies to JRE packages on all supported OS families and to JDK packages on
Debian-based systems.

Default:

```yaml
openjdk_headless: true
```

### `openjdk_version`

Type: `int`. Required: `false`.

OpenJDK major version to install from the distribution packages.

Default:

```yaml
openjdk_version: 25
```

## Check Mode

Reports required package installation without installing packages.

## Operational Notes

- Changing the type or version installs the new selection and leaves existing
  Java packages installed.

## Supported Platforms

| OS Family | Distribution | Version | Container Image |
| --------- | ------------ | ------- | --------------- |
| RedHat | AlmaLinux | latest | [jomrr/molecule-almalinux:latest](https://hub.docker.com/r/jomrr/molecule-almalinux) |
| Debian | Debian | latest | [jomrr/molecule-debian:latest](https://hub.docker.com/r/jomrr/molecule-debian) |
| RedHat | Fedora | latest | [jomrr/molecule-fedora:latest](https://hub.docker.com/r/jomrr/molecule-fedora) |
| Suse | OpenSuse Leap | latest | [jomrr/molecule-opensuse-leap:latest](https://hub.docker.com/r/jomrr/molecule-opensuse-leap) |
| Suse | OpenSuse Tumbleweed | latest | [jomrr/molecule-opensuse-tumbleweed:latest](https://hub.docker.com/r/jomrr/molecule-opensuse-tumbleweed) |
| Debian | Ubuntu | latest | [jomrr/molecule-ubuntu:latest](https://hub.docker.com/r/jomrr/molecule-ubuntu) |

## Example Playbook

### Install the default development kit

```yaml
---
- name: Install OpenJDK 25
  hosts: all
  gather_facts: true
  roles:
    - role: jomrr.openjdk
```

### Install a runtime with graphical support

```yaml
---
- name: Install the OpenJDK runtime
  hosts: all
  gather_facts: true
  roles:
    - role: jomrr.openjdk
      openjdk_type: jre
      openjdk_headless: false
      openjdk_version: 25
```

## Author

[Jonas Mauer](https://github.com/jomrr)

## License

This project is licensed under the MIT License.
See [LICENSE](LICENSE) for the full license text.

Copyright (c) 2021 Jonas Mauer.
