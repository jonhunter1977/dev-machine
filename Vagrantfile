# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Pick your virtual box image - https://atlas.hashicorp.com/boxes/search - is a good resource
  # config.vm.box = "box-cutter/ubuntu1404-desktop"
  config.vm.box = "box-cutter/ubuntu1604-desktop"

  config.vm.network "private_network", ip: "192.168.10.4"

  # set the name of your vm here
  config.vm.define "dev-machine" do |d|
  end

  # uncomment/copy the line below if you want to do any port forwarding
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # uncomment/copy the line below if you want to sync any host folders to the guest
  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--cableconnected1", "on"]

    # use host for internet connectivity
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]

    # Customize the amount of memory on the VM:
    vb.memory = "8192"
  end

  # provision the machine using ansible running on the guest
  # this will install ansible on the guest
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
  end
end
