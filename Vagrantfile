# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  # config.vm.network "forwarded_port", guest: 8081, host: 8081
  config.vm.network "forwarded_port", guest: 8443, host: 8443
  # config.vm.network "forwarded_port", guest: 8843, host: 8843
  # config.vm.network "forwarded_port", guest: 8880, host: 8880
  config.vm.network "public_network"

  config.vm.post_up_message = "Controller URL: https://localhost:8443/manage/"

  config.vm.provision "shell", inline: <<-shell
    echo "deb http://www.ubnt.com/downloads/unifi/debian stable ubiquiti" >> /etc/apt/sources.list.d/10unifi.list
    apt-key adv --keyserver keyserver.ubuntu.com --recv 06E85760C0A52C50
    apt update
    apt install -y unifi
    echo "# # # # # # # # # # # # # # # # # # # # # # # #"
    echo "# Provisioning Complete                       #"
    echo "# Controller software should be accessible at #"
    echo "# https://localhost:8443/manage/              #"
    echo "# # # # # # # # # # # # # # # # # # # # # # # #"
  shell
end
