# -*- mode: ruby -*-
# vim: set ft=ruby :

Vagrant.configure("2") do |config|
config.vm.define "client" do |client|
  client.vm.box = "centos/7"
  client.vm.box_version = "1804.02"
  client.vm.ignore_box_vagrantfile = true
  client.vm.hostname = "client"
  client.vm.synced_folder ".", "/vagrant", disabled: true
  client.vm.network "private_network", type: "dhcp"
  client.vm.provider "virtualbox" do |vb|
      vb.cpus = 1
      vb.memory = "512"
      vb.name = "client"
  end
 client.vm.provision "shell", inline: <<-SHELL
sudo su
#  mkdir /mnt/upload
#  mount -t nfs 192.168.1.100:/var/upload /mnt/upload
# touch /mnt/upload/Bendin
# mkdir /mnt/upload1
# mount -t nfs 192.168.1.100:/var/upload1 /mnt/upload1 -o udp
# touch /mnt/upload1/BEndin
                       SHELL


end

end
