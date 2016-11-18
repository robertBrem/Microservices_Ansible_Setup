# -*- mode: ruby -*-
# vi: set ft=ruby :

$memory = 4096
$cpus = 2
$hostname = "rob-01"
$gui = true

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
 # config.vm.box = "ubuntu/xenial64"
 # config.vm.box_url = "https://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-vagrant.box"
  config.vm.boot_timeout = 800
  config.vm.box = "boxcutter/ubuntu1604-desktop"
  config.vm.box_url = "https://atlas.hashicorp.com/boxcutter/ubuntu1604-desktop"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder ".", "/vagrant", disabled: false
  # config.vm.synced_folder "./my/location/on/host", "/vagrant/my/location"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = $gui
    # Customize the amount of memory on the VM:
    vb.memory = $memory
    # Customize the amount of memory on the VM:
    vb.cpus = $cpus
  end

  # set hostname
  config.vm.hostname = $hostname

  # set ip address
#  config.vm.network "private_network", ip: "172.1.1.200"

  # add ssh key to authorized_keys
  # config.ssh.insert_key = true
  # add user ssh key to authorized_keys
#  config.vm.provision "file", source: "./id_rsa.pub", destination: "/tmp/id_rsa.pub"
#  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
#  config.vm.provision :shell, :inline => "cat /tmp/id_rsa.pub >> /home/ubuntu/.ssh/authorized_keys"

  # Run Ansible from the Vagrant VM
  config.vm.provision "ansible_local" do |ansible|
    #ansible.playbook = "playbooks/basicSetUp.yml"
    ansible.playbook = "playbooks/test.yml"
    ansible.verbose        = true
    ansible.inventory_path = "hosts"
    ansible.limit = "all"
    ansible.version = "latest"
  end

end
