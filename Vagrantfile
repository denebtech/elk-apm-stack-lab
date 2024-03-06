# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box_check_update = false

  config.vm.define "elk" do |elk|
    elk.vm.hostname = "elkserver.local.com"
    elk.vm.box = "ubuntu/focal64"
    elk.vm.network :private_network, ip: "192.168.56.101"
    elk.vm.network "forwarded_port", guest: 9200, host: 1920
    elk.vm.network "forwarded_port", guest: 5601, host: 1560

    # provisioning
    elk.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
    config.vm.provision "file", source: "./docker/elk.yml", destination: "compose.yml"
    config.vm.provision "file", source: "./docker/.env", destination: ".env"

  end

  config.vm.define "webapp" do |webapp|
    webapp.vm.hostname = "webapp.local.com"
    webapp.vm.box = "ubuntu/focal64"
    webapp.vm.network :private_network, ip: "192.168.56.102"

    # provisioning
    webapp.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end

  config.vm.define "api" do |api|
    api.vm.hostname = "api.local.com"
    api.vm.box = "ubuntu/focal64"
    api.vm.network :private_network, ip: "192.168.56.103"

    # provisioning
    api.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8192"
    vb.cpus = 4
  end

end
