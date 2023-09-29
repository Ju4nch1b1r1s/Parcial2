Vagrant.configure("2") do |config|
 if Vagrant.has_plugin? "vagrant-vbguest"
 config.vbguest.no_install = true
 config.vbguest.auto_update = false
 config.vbguest.no_remote = true
 end

 config.vm.define :cliente do |cliente|
 cliente.vm.box = "generic/centos9s"
 cliente.vm.network :private_network, ip: "192.168.50.2"
 cliente.vm.hostname = "cliente"
 cliente.vm.synced_folder ".", "/vagrant"
 end

 config.vm.define :servidor do |servidor|
 servidor.vm.box = "generic/centos9s"
 servidor.vm.network "public_network"
 servidor.vm.network :private_network, ip: "172.16.0.3"
 servidor.vm.network :private_network, ip: "192.168.50.3"
 servidor.vm.network :forwarded_port, guest: 80, host:5567
 servidor.vm.network :forwarded_port, guest: 443, host:5568
 servidor.vm.hostname = "servidor"
 servidor.vm.synced_folder ".", "/vagrant"
 end
end
