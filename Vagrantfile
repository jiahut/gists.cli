# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "centos" do |centos|
    centos.vm.box = "centos-6.5"
    centos.vm.box_url = "https://dl.dropboxusercontent.com/u/26568959/VagrantBoxes/CentOS-6.5-i386.box"
    centos.vm.hostname = "centos"
    centos.vm.network "forwarded_port", guest: 22, host: 1234
    centos.vm.provision "ansible" do |ansible|
      ansible.inventory_path = "./_vagrant/vagrant_ansible_inventory_centos"
      ansible.playbook = "./_vagrant/centos.yml"
      ansible.sudo = true
#      ansible.verbose = 'v'
    end
  end

  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "ubuntu-12"
    ubuntu.vm.hostname = "ubuntu"
    ubuntu.vm.network "forwarded_port", guest: 22, host: 1235
    ubuntu.vm.box_url = "https://dl.dropboxusercontent.com/u/26568959/VagrantBoxes/Ubuntu-12.04.3-i386.box"
    ubuntu.vm.provision "ansible" do |ansible|
      ansible.inventory_path = "./_vagrant/vagrant_ansible_inventory_ubuntu"
      ansible.playbook = "./_vagrant/ubuntu.yml"
      ansible.sudo = true
#      ansible.verbose = 'v'
    end
  end

  config.vm.synced_folder "./", "/git_data"

  # config.vm.provider :virtualbox do |vb|
  #   # Don't boot with headless mode
  #   vb.gui = true
  #
  #   # Use VBoxManage to customize the VM. For example to change memory:
  #   vb.customize ["modifyvm", :id, "--memory", "1024"]
  # end
 
end
