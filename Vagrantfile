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
gcc \
git
wget https://nginx.org/packages/centos/7/SRPMS/nginx-1.14.1-1.el7_4.ngx.src.rpm
rpm -i nginx-1.14.1-1.el7_4.ngx.src.rpm
cd ~
wget --no-check-certificate https://www.openssl.org/source/openssl-1.1.1l.tar.gz
tar -xvf openssl-1.1.1l.tar.gz 
yum-builddep rpmbuild/SPECS/nginx.spec -y
rm -rf /root/rpmbuild/SPECS
cd /root/rpmbuild/
git clone https://github.com/BendinRS/SPECS.git
cd ~
rpmbuild -bb rpmbuild/SPECS/nginx.spec
yum localinstall -y \
rpmbuild/RPMS/x86_64/nginx-1.14.1-1.el7_4.ngx.x86_64.rpm
systemctl start nginx



                       SHELL


end

end
