Vagrant.configure(2) do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.network "forwarded_port", guest: 8080, host: 8880
  config.vm.network "private_network", ip: "192.168.56.10"
end
