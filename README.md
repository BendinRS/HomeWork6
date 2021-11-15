# HomeWork6

### Устанавливаем необходимые пакеты для выполнения домашней работы:

+ redhat-lsb-core 
+ wget 
+ rpmdevtools 
+ rpm-build 
+ createrepo 
+ yum-utils
+ gcc
+ nano

#### возьмем пакет NGINX и соберем его с поддержкой openssl

+ Загружаем srpm пакет
[root@client vagrant]# wget https://nginx.org/packages/centos/7/SRPMS/nginx-1.14.1-1.el7_4.ngx.src.rpm
+ При установке такого пакета в домашней директории создается древо каталогов для
сборки: 
[root@client vagrant]# rpm -i nginx-1.14.1-1.el7_4.ngx.src.rpm
+ Скачаем и разархивируем исходник для openssl
[root@client ~]# wget --no-check-certificate https://www.openssl.org/source/openssl-1.1.1l.tar.gz
[root@client ~]# tar -xvf openssl-1.1.1l.tar.gz 
+ Установим зависимости
[root@client ~]# yum-builddep rpmbuild/SPECS/nginx.spec -y









