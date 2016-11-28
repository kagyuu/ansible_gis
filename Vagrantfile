# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"

  config.vm.define "gis" do |server|
    server.vm.hostname = "gis"
    server.vm.network "forwarded_port", guest: 80, host: 10080
    server.vm.network "forwarded_port", guest: 5432, host: 15432
  end
end
