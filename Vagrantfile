# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "roboxes/debian11"
  config.vm.network "forwarded_port", guest:80, host:7080, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest:8000, host:8000, host_ip: "127.0.0.1"
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "1024"
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
