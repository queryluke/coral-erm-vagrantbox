# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'vagrant_config'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = VM_BOX
  config.vm.hostname = PROJECT_NAME

  config.ssh.forward_agent = 'true'

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: PRIVATE_NETWORK
  config.vm.network 'forwarded_port', guest: 80, host: LOCALHOST_PORT

  # main provisioner
  config.vm.provision "ansible_local" do |ansible|
    ansible.provisioning_path = '/provisioning'
    ansible.playbook = 'playbook.yml'
    ansible.inventory_path = 'inventory'
    ansible.galaxy_role_file = 'requirements.yml'
    ansible.limit = 'all'
    ansible.extra_vars = {
      project_name: PROJECT_NAME,
      php_version: PHP_VERSION,
      mysql_root_password: MYSQL_ROOT_PASSWORD,
      coral_dir: CORAL_DIR,
      clone_coral: CLONE_CORAL,
      coral_repo: CORAL_REPO,
      coral_branch: CORAL_BRANCH
    }
  end
end
