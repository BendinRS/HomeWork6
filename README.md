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
+ Так как я не знаю, как изменить конфиг рационально - извращаемся :)
[root@client rpmbuild]# rm -rf SPECS/
[root@client rpmbuild]# git clone https://github.com/BendinRS/SPECS.git

+ Собираем пакет

[root@client ~]# rpmbuild -bb rpmbuild/SPECS/nginx.spec
...
Записан: /root/rpmbuild/RPMS/x86_64/nginx-1.14.1-1.el7_4.ngx.x86_64.rpm
Записан: /root/rpmbuild/RPMS/x86_64/nginx-debuginfo-1.14.1-1.el7_4.ngx.x86_64.rpm
Выполняется(%clean): /bin/sh -e /var/tmp/rpm-tmp.AwlqOv
 umask 022
 cd /root/rpmbuild/BUILD
 cd nginx-1.14.1
 /usr/bin/rm -rf /root/rpmbuild/BUILDROOT/nginx-1.14.1-1.el7_4.ngx.x86_64
 exit 0
 
+ Устанавливаем и запускаем пакет nginx
[root@client ~]# yum localinstall -y \ 
> rpmbuild/RPMS/x86_64/nginx-1.14.1-1.el7_4.ngx.x86_64.rpm

...
Installed:
  nginx.x86_64 1:1.14.1-1.el7_4.ngx                                                                                                                   
[root@client ~]# systemctl start nginx

#### Создать свой репозиторий и разместить там ранее собранный RPM



 
 
 








