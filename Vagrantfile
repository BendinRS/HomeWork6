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
yum install -y \
redhat-lsb-core \
wget \
rpmdevtools \
rpm-build \
createrepo \
yum-utils \
gcc
wget https://nginx.org/packages/centos/7/SRPMS/nginx-1.14.1-1.el7_4.ngx.src.rpm
rpm -i nginx-1.14.1-1.el7_4.ngx.src.rpm
cd ~
wget --no-check-certificate https://www.openssl.org/source/openssl-1.1.1l.tar.gz
tar -xvf openssl-1.1.1l.tar.gz 
yum-builddep rpmbuild/SPECS/nginx.spec -y




#  mkdir /mnt/upload
#  mount -t nfs 192.168.1.100:/var/upload /mnt/upload
# touch /mnt/upload/Bendin
# mkdir /mnt/upload1
# mount -t nfs 192.168.1.100:/var/upload1 /mnt/upload1 -o udp
# touch /mnt/upload1/BEndin
                       SHELL


end

end
