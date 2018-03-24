# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'
vc = YAML.load_file('./config.yml')

Vagrant.configure(vc['vagrantfile_api_version']) do |config|

  config.vm.box = vc['vm_box']
  config.vm.hostname = vc['project_name']

  config.ssh.forward_agent = 'true'

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: vc['private_network']
  config.vm.network 'forwarded_port', guest: 80, host: vc['localhost_port']

  # main provisioner
  config.vm.provision "ansible_local" do |ansible|
    ansible.provisioning_path = '/vagrant/provisioning'
    ansible.playbook = 'playbook.yml'
    ansible.inventory_path = 'inventory'
    ansible.galaxy_role_file = 'requirements.yml'
    ansible.limit = 'all'
    ansible.extra_vars = {
      project_name: vc['project_name'],
      php_version: vc['php_version'],
      mysql_root_password: vc['mysql_root_password'],
      coral_dir: vc['coral_dir'],
      clone_coral: vc['clone_coral'],
      coral_repo: vc['coral_repo'],
      coral_branch: vc['coral_branch']
    }
  end
end
