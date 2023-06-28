# Queerious Labs Infrastructure

Documentation and ansible confguration for the tech / IT infrastructure
at Queerious Labs

## Ansible

### Inventory
`ansible/ansible.cfg` sets the default inventory to use as `hosts.yml`.  Use the `-i` switch to select something different e.g. `vm.yml`.

```bash
$ cd ansible
ansible$ ansible-playbook -i vm.yml playbooks/00-utils.yml
```

### Secrets
Secrets are stored in the repository using `ansible-vault` and the vault password may be stored
in `ansible/.passwd`, as configured in `ansigle.cfg`.  Note that whitespace after the password doesn't 
matter.


### Examples
Test your connection to infrastructure by pinging all hosts

```bash
ansible/$ ansible all -m ping
```

Run all playbooks (i.e. configure all infrastructure)

```bash
.../ansible$ ansible-playbook playbooks/all.yml
```

## Vagrant
Vagrant may be used to create a local, virtualized machine to test.

Vagrant is not a virutalization engine, but a manager of virtualization engines.  It requires at least one virutalization engine to run, e.g. `virtualbox` or `libvirt`.

The included `vm.yml` inventory may require customization depending on your vagrant provider.  Specifically you will need to edit teh `ansible_ssh_private_key_file` to point to the private key created by vagrant to deploy to the vm.  The included `vm.yml` uses a `libvirt` provider, but this will be different if, for example, `virtualbox` is used.

The vm is not automically provisioned using vagrant's ansible capabilities, as the goal is to test the ansible provisioning itself, not create a provisioned box.  After the vm is brought up:

```bash
$ vagrant up
```

Inspect the machine via ssh
```bash
$ vagrant ssh
```

The deployment may be tesed from the `ansible` directory using the `vm.yml` inventory

```bash
.../ansible$ ansible-playbook -i vm.yml playbooks/all.yml
```
