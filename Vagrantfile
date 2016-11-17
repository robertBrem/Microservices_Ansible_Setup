# -*- mode: ruby -*-
# vi: set ft=ruby :

$instances = 1
$memory = 1024
$cpus = 1
$hostname = "rob"
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
  config.vm.box = "ubuntu/xenial64"
 # config.vm.box_url = "https://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-vagrant.box"

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
    vb.gui = false
    # Customize the amount of memory on the VM:
    vb.memory = $memory
    # Customize the amount of memory on the VM:
    vb.cpus = $cpus
    # install gui
    vb.gui = $gui
  end

#  (1..$instances).each do |i|
#    config.vm.define vm_name = $hostname+"-%02d" % i do |ubuntu|
#      ubuntu.vm.hostname = vm_name

      # Create a private network, which allows host-only access to the machine
      # using a specific IP.
#      ubuntu.vm.network "private_network", ip: "172.1.1.#{i+100}"

      # Create a forwarded port mapping which allows access to a specific port
      # within the machine from a port on the host machine. In the example below,
      # accessing "localhost:8080" will access port 80 on the guest machine.
      # config.vm.network "forwarded_port", guest: 80, host: 8080

      # Create a public network, which generally matched to bridged network.
      # Bridged networks make the machine appear as another physical device on
      # your network.
      # config.vm.network "public_network"
      #
#    end
#  end

#  config.vm.provision "shell", inline: "sed -i 's/us.archive.ubuntu/au.archive.ubuntu/g' /etc/apt/sources.list && apt-get update && apt-get install ansible -y"

  # Run Ansible from the Vagrant VM
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbooks/basicSetUp.yml"
    ansible.verbose        = true
    ansible.inventory_path = "hosts"
    ansible.limit = "all"
    ansible.version = "latest"
  end

end
