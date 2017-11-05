# CORAL ERM Vagrant VM
Vagrant config for quickly setting up a CORAL dev environment

`$PROJECT_ROOT` is the dir containing the `Vagrantfile`

1. Download and Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
2. Download and Install [Vagrant](https://www.vagrantup.com/downloads.html)
3. Install the necessary Vagrant plugins
    * [Guest Additions](https://github.com/dotless-de/vagrant-vbguest) `vagrant plugin install vagrant-vbguest`
    * [Host Manager](https://github.com/devopsgroup-io/vagrant-hostmanager) `vagrant plugin install vagrant-hostmanager`
4. Clone your fork of the [CORAL ERM](https://github.com/Coral-erm) repo into or unzip a release into `$PROJECT_ROOT`. It should be named `coral`
5. Create the VM:
    * `$ cd $PROJECT_ROOT; vagrant up`
    
Install coral using the gui at http://coral.dev
Mysql user and password:
* user=root
* password=coralerm

Changes you make in the /coral project dir will be automatically synced on to the VM.