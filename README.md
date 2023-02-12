# Queerious Labs Infrastructure

Documentation and ansible confguration for the tech / IT infrastructure
at Queerious Labs

## Ansible

Ansible needs to be told which inventory file to use using `-i` (by default is uses /etc/ansible/hosts).

E.g: To test your connection to infrastructure by pinging all hosts, run:

```bash
cd ansible
ansible all -m ping
```

Secrets are stored in the repository using `ansible-vault` and the vault password may be stored
in `ansible/.passwd`, as configured in `ansigle.cfg`.  Note that whitespace after the password doesn't 
matter.

Or to run all playbooks (i.e. configure all infrastructure):

```bash
cd ansible
ansible-playbook playbooks/all.yml
```
