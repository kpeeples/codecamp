# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  #config.vm.box = "ubuntu/trusty64"
  config.vm.box = "bento/centos-6.7"
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.name = "apache"
    v.memory = 512
    v.cpus = 2
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  config.vm.hostname = "apache"
  config.vm.network :private_network, ip: "192.168.33.34"

  # Set the name of the VM. See: http://stackoverflow.com/a/17864388/100134
  config.vm.define :apache do |apache|
  end

end