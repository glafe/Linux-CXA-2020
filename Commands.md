## Launching a Docker container

docker build -t webserver .
docker images
docker run -d webserver

## Viewing GRUB configuration files

less /boot/grub/grub.cfg
less /etc/default/grub
ls /etc/grub.d
sudo update-grub

## Controling runtime levels

sudo telinit 0 
systemctl get-default
sudo systemctl isolate rescue.target 
sudo systemctl enable multi-user.target 

## Controlling system locale

less /usr/share/i18n/locales/en_CA
localectl status
localectl list-locales
localectl set-locale LANG=en_CA.utf8

## Controlling the system timezone

timedatectl
timedatectl list-timezones | grep -i america
timedatectl set-timezone Canada/Toronto
## Discover and mount a storage volume

df -ht ext4
lsblk | grep sd
sudo mkdir /media/newplace
sudo mount /dev/sdb2 /media/newplace
## Working with package managers
### [on Ubuntu]
less /etc/apt/sources.list
apt list --all-versions | wc
apt update
apt search business card | less
apt show glabels
apt install glabels
apt-get install glabels [don't run]
### [on CentOS]
yum list vino
yum info vino
yum install vino
yum info trousers
## Working with LXD containers
### [on Ubuntu]
sudo apt install lxd
sudo lxc launch images:centos/7/amd64 centos7
sudo lxc list
sudo lxc exec centos7 /bin/bash
Install and launch Apache

### [On CentOS]
yum install httpd 
systemctl start httpd
systemctl enable httpd
##Compiling software packages

sudo apt install autoconf g++ subversion linux-source linux-headers-`uname -r` \
  build-essential tofrodos git-core subversion dos2unix make gcc automake cmake \
  checkinstall git-core dpkg-dev fakeroot pbuilder dh-make debhelper devscripts \
  patchutils quilt git-buildpackage pristine-tar git yasm checkinstall cvs mercurial

wget https://nmap.org/dist/nmap-7.70.tgz
tar xzf nmap-7.70.tgz
cd nmap-7.70
./configure
make
make install

## Dockerfile contents:
FROM ubuntu:18.04
RUN apt-get update
RUN apt-get install -y apache2
ADD index.html /var/www/html/
CMD /usr/sbin/apache2ctl -D FOREGROUND
EXPOSE 80
