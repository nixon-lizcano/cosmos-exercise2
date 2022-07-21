# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.require_version ">= 2.2.19"

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false

  # Disables default sync folder, it just slows down provisioning
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # Main ansible playbook (just update & sinchronize time)
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "site.yml"
  end

  config.vm.define "db" do |db|
    db.vm.box = "bento/ubuntu-22.04"
    db.vm.hostname = "dbserver"
    db.vm.network "private_network", ip: "192.168.56.11", hostname: true

    db.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "db.yml"
    end
  end

  config.vm.define "web" do |web|
    web.vm.box = "bento/ubuntu-22.04"
    web.vm.network "private_network", ip: "192.168.56.10", hostname: true
    web.vm.hostname = "webserver"

    web.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "web.yml"
    end
  end
end
