Vagrant.configure("2") do |config|

  config.vm.define "jumpbox" do |jumpbox|
    jumpbox.vm.box = "generic/debian12"
    jumpbox.vm.network :private_network, ip: "192.168.56.100"
    jumpbox.vm.disk :disk, size: "10GB", primary: true
    jumpbox.vm.provider "virtualbox" do |vb|
      vb.name = "jumpbox"
      vb.memory = "512"
      vb.cpus = 1
      vb.linked_clone = true
    end
  end

  config.vm.define "server" do |server|
    server.vm.box = "generic/debian12"
    server.vm.network :private_network, ip: "192.168.56.110"
    server.vm.network "forwarded_port", guest: 6443, host: 6443
    server.vm.disk :disk, size: "20GB", primary: true
    server.vm.provider "virtualbox" do |vb|
      vb.name = "server"
      vb.memory = "2048"
      vb.cpus = 1
      vb.linked_clone = true
    end
  end

  config.vm.define "node-0" do |node|
    node.vm.box = "generic/debian12"
    node.vm.network :private_network, ip: "192.168.56.111"
    node.vm.disk :disk, size: "20GB", primary: true
    node.vm.provider "virtualbox" do |vb|
      vb.name = "node-0"
      vb.memory = "2048"
      vb.cpus = 1
      vb.linked_clone = true
    end
  end

  config.vm.define "node-1" do |node|
    node.vm.box = "generic/debian12"
    node.vm.network :private_network, ip: "192.168.56.112"
    node.vm.disk :disk, size: "20GB", primary: true
    node.vm.provider "virtualbox" do |vb|
      vb.name = "node-1"
      vb.memory = "2048"
      vb.cpus = 1
      vb.linked_clone = true
    end
  end
end
