# Ransomable

Ansible playbook to setup report generation pipeline on a Ubuntu host.

 - System dependencies.
 - R dependencies
 - Ruby dependencies.
 - Install SIMPL pacakges from bitbucket.
 - Install systemd services and time to orchestrate pipeline.

## Use
1. Create inventory/hosts.yml file with appropriate host domain or ip.
1. Install depencencies `ansible-galaxy -r requirements.yml`
1. Run `ansible-playbook -i inventory/hosts.yml playbook.yml`

## Testing with Vagrant
### Create Vanilla Ubuntu VM
Bring up a vm instance without using the vagrant provisioner.
Using the vagrant provisioner to run the playbook will fail when 
the playbook waits locally for the vm to reboot.

```
vagrant up --no-provision
```

### Run Ansible on the VM
Install the external roles as above
```
ansible-galaxy -r requirements.yml
```

Run ansible with the full playbook indicating the vagrant host using an inventory file.
The vagrant inventory file specifies the host address, port, and connection user (vagrant).
It also specifies ssh options that would be dangerous if it weren't a local vm.
```
ansible-playbook -i inventory/vagrant-inv.yml playbook.yml
```

### SSH into VM
The VM can be investigated by running
```
vagrant ssh
```

### Shutdown and cleanup
Shutting down the VM to save it for later is done with `halt`
```
vagrant halt
```

Removing the VM completely is done with `destroy`
```
vagrant destroy
```
