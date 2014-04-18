# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Every Vagrant virtual environment requires a box to build off of.

 config.vm.define :zenoss do |zenoss_config|
    zenoss_config.vm.box = "chef/centos-6.5"
    zenoss_config.vm.hostname = "zenoss"
    zenoss_config.vm.network "private_network", ip: "192.168.50.50"

    zenoss_config.vm.provision "ansible" do |ansible|
        ansible.playbook = "zenoss-vagrant.yml"
        ansible.sudo = true
        #ansible.verbose = "vvvv"
        ansible.groups = {
          "vagrant" => ["zenoss"],
        }
        ansible.extra_vars = {
          "virtualbox_client" => true
        }
    end

  end
end
