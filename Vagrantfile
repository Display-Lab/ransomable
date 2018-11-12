# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"
  config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = false
  
    # Customize the amount of memory on the VM:
    vb.memory = "2048"

    # Don't sync folders
    config.vm.synced_folder "", "", disabled: true
  end
  
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.groups = {
      "reports" => ["default"]
    }
    ansible.extra_vars = {
      apt_key_server: 'hkps://keyserver.ubuntu.com:443',
      apt_key_id: '51716619E084DAB9'
    }
  end
end
