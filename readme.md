# Ransomable

Ansible playbook to provision ubuntu machine with R and Ruby dependencies.

## Use

1. Create hosts.yml file with host domain or ip to provision.
1. Run `ansible-playbook playbook.yml`

## Installing Dependencies

Use ansible galaxy to install the roles this playbook depends upon.

```
ansible-galaxy -r requirements.yml
```
