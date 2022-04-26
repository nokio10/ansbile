# -*- mode: ruby -*-
# vim: set ft=ruby :
MACHINES = {
:ansible => {
:box_name => "centos/7",
:box_version => "2004.01",
#:provision => "test.sh",
},
}
Vagrant.configure("2") do |config|
MACHINES.each do |boxname, boxconfig|
#config.vm.synced_folder ".", "/vagrant", disabled: false
config.vm.define boxname do |box|
box.vm.box = boxconfig[:box_name]
box.vm.box_version = boxconfig[:box_version]
box.vm.host_name = "ansible"
box.vm.provider :virtualbox do |vb|
box.vm.network "forwarded_port", guest: 22, host: 2201
box.vm.network "forwarded_port", guest: 8081, host: 8080
vb.customize ["modifyvm", :id, "--memory", "2048"]
needsController = false
box.vm.provision "shell", inline: <<-SHELL
sudo mkdir ~/.ssh
cat /vagrant/id_rsa.pub > /root/.ssh/authorized_keys
SHELL
end
end
end
end
