# Cisco IOS Ansible Examples

The repository contains examples of Ansible roles used to configure different items on Cisco IOS networking equipment.

Sensitive credentials are encrypted using Ansible vault and are not stored in this repo. Example secrets.yaml files are provided with instructions on how to use ansible vault.

When creating a new variable, if it's common among the entire group, they're stored in group_vars otherwise, they're stored in the individual host_vars directory.

Roles Covered:

- Configure NTP Servers
- Setup DNS Servers
- Configure Layer 2 Interfaces
- Configure Layer 3 Interfaces
- Set Interface Description based on Current CDP/LLDP Neighbors
- Get Running Config
- Save Running Config to Startup Config

## Prerequisites

1) OS that is not Windows - [WSL FTW](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
2) Ansible 2.8.4
3) Python 3.7.4
4) Pipenv or other virtual environment

## Installing

Clone this repo

```bash
$ git clone https://github.com/mtbutler07/ansible-ios.git
```

Install [Python 3.7.3](https://www.python.org/downloads/release/python-373/)

Install [Pipenv](https://docs.pipenv.org/en/latest/) using Pip

```bash
$ python3 -m pip install pipenv -U --user
```

Install dependencies using Pipenv

```bash
$ pipenv install
$ pipenv shell
```

OR install dependencies using pip

```bash
$ python3 -m pip install -r requirements.txt -U --user
```

Modify the Username, Password, and Enable Password in the sample host_vars secret file to for your environment.
Rename the file to secrets.yaml
Encrypt using Ansible Vault

```bash

$ cd inventory/host_vars/lab_switch
$ nano secrets.example.yaml
$ mv secrets.example.yaml secrets.yaml

$ ansible-vault encrypt secrets.yaml

  New Vault password: hunter2
  Confirm New Vault password: hunter2
  Encryption successful
```

## Usage

Run the full Ansible playbook

```bash
$ ansible-playbook ios_playbook -i inventory/homelab --ask-vault-pass

  Vault password: hunter2
```

## Authors

**Marcus Butler**

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

