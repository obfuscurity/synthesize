# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "synthesize"
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/saucy/current/saucy-server-cloudimg-amd64-vagrant-disk1.box"
  config.vm.network :forwarded_port, guest: 443, host: 8443
  config.vm.network :forwarded_port, guest: 8125, host: 8125
  config.vm.network :forwarded_port, guest: 2003, host: 22003
  config.vm.network :forwarded_port, guest: 2004, host: 22004
  config.vm.provision "shell", inline: "cd /vagrant; sudo ./install"
end
