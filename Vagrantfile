# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box_check_update = false

  config.vm.define "elk" do |elk|
    elk.vm.hostname = "elkserver.local.com"
    elk.vm.box = "ubuntu/focal64"
    elk.vm.network :private_network, ip: "192.168.56.101"

    elk.vm.provision "shell", inline: <<-SHELL
      sudo apt update
    SHELL
  end

  config.vm.define "webapp" do |webapp|
    webapp.vm.hostname = "webapp.local.com"
    webapp.vm.box = "ubuntu/focal64"
    webapp.vm.network :private_network, ip: "192.168.56.102"

    webapp.vm.provision "shell", inline: <<-SHELL
      sudo apt update
    SHELL
  end

  config.vm.define "api" do |api|
    api.vm.hostname = "api.local.com"
    api.vm.box = "ubuntu/focal64"
    api.vm.network :private_network, ip: "192.168.56.103"

    api.vm.provision "shell", inline: <<-SHELL
      sudo apt update
    SHELL
  end

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8192"
    vb.cpus = 4
  end

end
