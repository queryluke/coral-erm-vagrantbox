# CORAL ERM Vagrant VM
Vagrant config for quickly setting up a CORAL dev environment

`$PROJECT_ROOT` is the dir containing the `Vagrantfile`

## Requirements
1. [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
2. [Vagrant](https://www.vagrantup.com/downloads.html)

## Usage
1. Move to the project root: `$ cd $PROJECT_ROOT; vagrant up`
2. Create a vagrant config file: `$ cp config.yml.example config.yml`
3. (_OPTIONAL_): Edit the `config.yml` file
4. `$ vagrant up`
    
Install coral using the gui at http://localhost:8777 (or at the `localhost_port` in the config)
Mysql user and password:
* user=root
* password=coralerm (_or the mysql_root_password you set in the config.yml file_)

## Config Options

There are 2 ways to utilize this box:

1. Develop within the vagrantbox. Set `clone_coral` to `true`. Edit files and issue git commands from within
the vagrant box.

2. Develop files locally. Set `clone_coral` to `false`. Edit files in an separate directory, using an IDE or script to sync
edits to the vagrant box.

|Option|Default|Description|
|---|---|---|
|`vagrantfile_api_version`|2|The api version used to run the vagrant file|
|`vm_box`|centos/7|A valid [Vagrant Box](https://app.vagrantup.com/boxes/search)|
|`private_network`|192.168.30.205|The IP to run the private network. Should be within `192.168.*.*`|
|`localhost_port`|8777|The port at which the application can be accessed. E.g. `http://localhost:8777`|
|`project_name`|coral|The project name, used in various provisioning scripts|
|`php_version`|7.1|The php version to install, must be >= 5.6|
|`mysql_root_password`|coralerm|The root password for the mysql installation|
|`clone_coral`|false|If set to true, it will clone a coral instance into the `coral_repo`|
|`coral_repo`|https://github.com/coral-erm/coral.git|The coral repo to clone, only used if `clone_coral` is set to true|
|`coral_branch`|master|Will checkout this branch after cloning coral|
|`coral_dir`|/coral|The location on the serve to clone coral|
