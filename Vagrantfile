# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "centos/7"
  config.vm.hostname = "coral"
  config.vm.synced_folder "./coral", "/coral", nfs: true

  config.ssh.forward_agent = "true"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.30.205"

  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.manage_guest = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true
  config.hostmanager.aliases = "#{config.vm.hostname}.dev"

  # main provisioner
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = 'provisioning/playbook.yml'
    ansible.inventory_path = "provisioning/inventory"
    ansible.limit = 'all'
  end
end
