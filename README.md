# Ansible playbook: labocbz.bootstrap_server

![Licence Status](https://img.shields.io/badge/licence-MIT-brightgreen)
![CI Status](https://img.shields.io/badge/CI-success-brightgreen)
![Testing Method](https://img.shields.io/badge/Testing%20Method-Ansible%20Molecule-blueviolet)
![Testing Driver](https://img.shields.io/badge/Testing%20Driver-docker-blueviolet)
![Language Status](https://img.shields.io/badge/language-Ansible-red)
![Compagny](https://img.shields.io/badge/Compagny-Labo--CBZ-blue)
![Author](https://img.shields.io/badge/Author-Lord%20Robin%20Crombez-blue)

## Description

![Tag: UNIX](https://img.shields.io/badge/Tech-UNIX-orange)
![Tag: Debian](https://img.shields.io/badge/Tech-Debian-orange)
![Tag: Ubuntu](https://img.shields.io/badge/Tech-Ubuntu-orange)
![Tag: Boilerplate](https://img.shields.io/badge/Tech-Boilerplate-orange)
![Tag: Bootstrap](https://img.shields.io/badge/Tech-Bootstrap-orange)
![Tag: SSL/TLS](https://img.shields.io/badge/Tech-SSL%2FTLS-orange)
![Tag: Byobu](https://img.shields.io/badge/Tech-Byobu-orange)
![Tag: Fail2ban](https://img.shields.io/badge/Tech-Fail2ban-orange)
![Tag: Lynis](https://img.shields.io/badge/Tech-Lynis-orange)
![Tag: Portsentry](https://img.shields.io/badge/Tech-Portsentry-orange)
![Tag: Postfix](https://img.shields.io/badge/Tech-Postfix-orange)
![Tag: Rsyslog](https://img.shields.io/badge/Tech-Rsyslog-orange)
![Tag: Unattended-Upgrades](https://img.shields.io/badge/Tech-Unattended--Upgrades-orange)
![Tag: Logrotate](https://img.shields.io/badge/Tech-Logrotate-orange)
![Tag: Rkhunter](https://img.shields.io/badge/Tech-Rkhunter-orange)
![Tag: Logwtach](https://img.shields.io/badge/Tech-Logwtach-orange)
![Tag: Node Exporter](https://img.shields.io/badge/Tech-Node--Exporter-orange)

An Ansible playbook to bootstrap and configure a server based on Debian/Ubuntu.

This Ansible playbook is an essential tool for automating and industrializing the deployment of servers and virtual machines. It relies on roles defined elsewhere in the documentation to simplify the process of bootstrapping, installing, configuring, and deploying a set of tools.

The approach of this playbook is based on organizing servers into groups, where each server must belong to one or more groups to be considered a target for tool installation and configuration. For example, by using the expression {{ tower_env | default([]) }}:&LOGWATCH, all servers that are part of the tower_env group and also present in the LOGWATCH group will automatically be equipped with the Logwatch tool, with consistent installation and configuration.

The primary goal of this playbook is to streamline and accelerate the setup of servers and virtual machines, ensuring uniformity in configuration and automating many tasks. This approach saves valuable time and reduces human errors when deploying complex IT infrastructures.

By using Ansible with this playbook and its associated roles, system administrators can deploy uniform and reliable architectures more quickly, contributing to more efficient management of the entire infrastructure.

## Deployment diagramm

Deployment diagram is not applicable for this case.

## Tests and simulations

### Basics

You have to run multiples tests. *tests with an # are mandatory*

```MARKDOWN
# lint
# syntax
# converge
# idempotence
# verify
side_effect
```

Executing theses test in this order is called a "scenario" and Molecule can handle them.

Molecule use Ansible and pre configured playbook to create containers, prepare them, converge (run the playbook) and verify its execution.
You can manage multiples scenario with multiples tests in order to get a 100% code coverage.

This playbook contains a ./tests folder. In this folder you can use the inventory or the tower folder to create a simualtion of a real inventory and a real AWX / Tower job execution.

### Command reminder

```SHELL
# Check your YAML syntax
yamllint -c ./.yamllint .

# Check your Ansible syntax and code security
ansible-lint --config=./.ansible-lint .

# Execute and test your playbook
molecule lint
molecule create
molecule list
molecule converge
molecule verify
molecule destroy

# Execute all previous task in one single command
molecule test
```

## Installation

To install this playbook, just copy/import this playbook or raw file into your fresh playbook repository or call it with the "include_playbook/import_playbook" module.

## Usage

### Vars

```YAML
# From inventory
---
# all vars from to put/from your inventory and groups,
# see tests/inventory/group_var for all groups and vars.
```

```YAML
# From AWX / Tower
---
tower_env: "local"
```

## Architectural Decisions Records

Here you can put your change to keep a trace of your work and decisions.

### 2023-09-22: First Init

* First init of this playbook with the bootstrap_playbook playbook by Lord Robin Crombez
* Playbook use all roles defined in se Sources section
* Playbook use a env target + group target to deploy on specific hosts and group
* Change can be done, maybe put all in inside play, but for my point of view, its better to be able to assign any host in any group

### 2023-10-06: New CICD, new Images

* New CI/CD scenario name
* Molecule now use remote Docker image by Lord Robin Crombez
* Molecule now use custom Docker image in CI/CD by env vars
* New CICD with needs and optimization

## Authors

* Lord Robin Crombez

## Sources

* [Ansible playbook documentation](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_playbooks.html)
* [Ansible Molecule documentation](https://molecule.readthedocs.io/)
* [labocbz.prepare_host](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Prepare-Host.git)
* [labocbz.add_certificates](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Add-Certificates.git)
* [labocbz.install_byobu](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Byobu.git)
* [labocbz.install_fail2ban](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Fail2ban.git)
* [labocbz.install_filebeat](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Filebeat.git)
* [labocbz.install_lynis](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Lynis.git)
* [labocbz.install_portsentry](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Portsentry.git)
* [labocbz.install_postfix](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Postfix.git)
* [labocbz.install_rsyslog](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Rsyslog.git)
* [labocbz.install_ssh](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-SSH.git)
* [labocbz.install_unattended_upgrades](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-UnattendedUpgrades.git)
* [labocbz.add_logrotate_confs](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Add-Logrotate-Confs.git)
* [labocbz.install_node_exporter](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Node-Exporter.git)
* [labocbz.install_rkhunter](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Rkhunter.git)
* [labocbz.install_logwtach](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Logwtach.git)
