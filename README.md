# Queerious Labs Infrastructure

Documentation and ansible confguration for the tech / IT infrastructure
at Queerious Labs

## Ansible

Ansible needs to be told which inventory file to use using `-i` (by default is uses /etc/ansible/hosts).

E.g: To test your connection to infrastructure by pinging all hosts, run:

```bash
cd ansible
ansible -i hosts all -m ping
```