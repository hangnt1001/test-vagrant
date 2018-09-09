# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"
VAGRANT_IP = "10.10.10.20"
VAGRANT_FOLDER = "/webapps/devops"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.define "web01" do |web01|
      web01.vm.boot_timeout = 900
      web01.vm.box = "ubuntu/trusty64"
      web01.vm.network :private_network, ip: VAGRANT_IP
      web01.vm.hostname = "web01"    
      web01.vm.synced_folder ".", VAGRANT_FOLDER
      web01.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.name = "web01"
      end
      web01.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = "provisioning/playbook.yml"
        ansible.inventory_path = "provisioning/inventory"
      end
    end
  end