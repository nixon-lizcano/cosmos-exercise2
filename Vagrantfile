# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.require_version ">= 2.2.19"

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false

  # Disables default sync folder, it just slows down provisioning
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.box = "bento/ubuntu-22.04"
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.vault_password_file = "vault.key"
    ansible.playbook = "ansible/main.yml"
    ansible.inventory_path = "ansible/host.ini"
  end

  config.vm.define "db" do |db|
    db.vm.hostname = "dbserver"
    db.vm.network "private_network", ip: "192.168.56.11", hostname: true

    db.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "ansible/db.yml"
      ansible.vault_password_file = "vault.key"
      ansible.inventory_path = "ansible/host.ini"
    end
  end

  config.vm.define "nfs" do |nfs|
    nfs.vm.hostname = "nfs"
    nfs.vm.network "private_network", ip: "192.168.56.13", hostname: true

    nfs.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "ansible/nfs.yml"
      ansible.vault_password_file = "vault.key"
      ansible.inventory_path = "ansible/host.ini"
    end
  end

  config.vm.define "web1" do |web|
    web.vm.hostname = "webserver1"
    web.vm.network "private_network", ip: "192.168.56.10", hostname: true

    web.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "ansible/web.yml"
      ansible.vault_password_file = "vault.key"
      ansible.inventory_path = "ansible/host.ini"
    end
  end

  config.vm.define "web2" do |web|
    web.vm.hostname = "webserver2"
    web.vm.network "private_network", ip: "192.168.56.12", hostname: true

    web.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "ansible/web.yml"
      ansible.vault_password_file = "vault.key"
      ansible.inventory_path = "ansible/host.ini"
    end
  end
end
