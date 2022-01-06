# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  
  config.vm.define "node1" do |node1|
    node1.vm.hostname = "node1"
    node1.vm.network "public_network", ip: "192.168.15.110", hostname: true, bridge: "enp1s0" 
    node1.vm.provision "file", source: "~/.ssh/id_ed25519.pub", destination: "/home/vagrant/.ssh/id_ed25519.pub"
    node1.vm.provision :shell, :inline => "cat /home/vagrant/.ssh/id_ed25519.pub >> /home/vagrant/.ssh/authorized_keys", run: "always"
  end
  
  config.vm.define "node2" do |node2|
    node2.vm.hostname = "node1"
    node2.vm.network "public_network", ip: "192.168.15.111", hostname: true, bridge: "enp1s0"
    node2.vm.provision "file", source: "~/.ssh/id_ed25519.pub", destination: "/home/vagrant/.ssh/id_ed25519.pub"
    node2.vm.provision :shell, :inline => "cat /home/vagrant/.ssh/id_ed25519.pub >> /home/vagrant/.ssh/authorized_keys", run: "always"
  end
end
