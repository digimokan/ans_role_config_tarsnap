# ans_role_config_tarsnap

Install the Tarsnap backup program, and configure backups.

[![Release](https://img.shields.io/github/release/digimokan/ans_role_config_tarsnap.svg?label=release)](https://github.com/digimokan/ans_role_config_tarsnap/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Requirements](#requirements)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
* [Role Options](#role-options)
* [Role Dependencies](#role-dependencies)
* [Contributing](#contributing)

## Purpose

* Install the [Tarsnap](https://www.tarsnap.com/) backup program.
* Simplify Tarsnap usage by providing a utility script.
* Optionally configure automatic periodic backups.

## Requirements

* An account created on tarsnap.com, for `tarsnap_user_id`.
* The role will prompt for the tarsnap.com account password, when doing the
  one-time action of creating the local machine key.
* After the role executes, ensure the created local machine key is backed up to
  a USB stick and printed paper copy.
* See [`defaults/main.yml`](../defaults/main.yml) for local machine key file
  path.

## Supported Operating Systems

* Arch Linux.

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_config_tarsnap
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the role like any local role, from the project playbook:

   ```yaml
   # playbook.yml
   - hosts: localhost
     connection: local
     tasks:
       - name: "Install the Tarsnap backup program, and configure backups"
         ansible.builtin.include_role:
           name: ans_role_config_tarsnap
         vars:
           user_name: "user2"
           tarsnap_user_id: "somebody@gmail.com"
           tarsnap_machine_label: "user2_dell_desktop"
   ```

## Role Options

See the role `defaults` file, for overridable vars:

  * [defaults/main.yml](../defaults/main.yml)

Define these _required_ vars for the role:

  * `user_name`: login account name, on the host machine
  * `tarsnap_user_id`: email address (tarsnap.com account id), can associate to multiple machines
  * `tarsnap_machine_label`: label for this machine, associated with machine key (an alphanumeric string)

## Role Dependencies

* [ans_role_config_cron](https://github.com/digimokan/ans_role_config_cron)
* [ans_role_config_unofficial_packages](https://github.com/digimokan/ans_role_config_unofficial_packages)

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_config_tarsnap/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).

