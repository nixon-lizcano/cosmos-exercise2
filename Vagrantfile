# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "web" do |web|
    web.vm.box = "bento/ubuntu-22.04"
    web.vm.network "private_network", ip: "192.168.56.10", hostname: true
    web.vm.hostname = "webserver"
  end

  config.vm.define "db" do |db|
    db.vm.box = "bento/ubuntu-22.04"
    db.vm.hostname = "dbserver"
    db.vm.network "private_network", ip: "192.168.56.11", hostname: true
  end

end
