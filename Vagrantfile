$mingw = <<-SCRIPT

PACKAGES=" \
  mingw32-gcc        \
  mingw32-cairo      \
  zip"

yum -y update
yum -y install $PACKAGES

MINGW_HOME=/usr/i686-w64-mingw32/sys-root/mingw

cp -r /vagrant/guacamole $MINGW_HOME/include
cp -r /vagrant/bin/* $MINGW_HOME/bin
cp -r /vagrant/bin/libguac-12.dll $MINGW_HOME/lib/libguac.a

SCRIPT


Vagrant.configure("2") do |config|
  config.vm.define "mingw" do |x|
    x.vm.box = "generic/centos7"
    x.vm.synced_folder ".", "/vagrant"
    x.vm.provision "shell", inline: $mingw
  end
end
