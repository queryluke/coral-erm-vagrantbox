# CORAL ERM Vagrant VM
A VM for quickly provisioning a CORAL ready server.

`$PROJECT_ROOT` is the dir containing the `Vagrantfile`

1. Download and Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
2. Download and Install [Vagrant](https://www.vagrantup.com/downloads.html)
3. Install [Ansible](http://docs.ansible.com/ansible/latest/intro_installation.html)
    * On a mac, you can use homebrew `brew install ansible`
4. Clone your fork of the [CORAL ERM](https://github.com/Coral-erm) repo into or unzip a release into `$PROJECT_ROOT`. It should be named `coral`
6. Install the necessary Ansible roles for this profile: 
    * `$ ansible-galaxy install -r $PROJECT_ROOT/requirements.yml`
7. Create the VM:
    * `$ cd $PROJECT_ROOT; vagrant up`
    
Install coral using the gui at https://coral.dev
Mysql user and password:
* user=root
* password=coralerm