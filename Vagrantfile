# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.require_version ">= 2.2.19"

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false

  config.vm.define "db" do |db|
    db.vm.box = "bento/ubuntu-22.04"
    db.vm.hostname = "dbserver"
    db.vm.network "private_network", ip: "192.168.56.11", hostname: true

    web.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "db-playbook.yml"
    end
  end

  config.vm.define "web" do |web|
    web.vm.box = "bento/ubuntu-22.04"
    web.vm.network "private_network", ip: "192.168.56.10", hostname: true
    web.vm.hostname = "webserver"

    web.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "web-playbook.yml"
    end
  end
end
