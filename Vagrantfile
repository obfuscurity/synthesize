# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "mayflower/trusty64-puppet3"
  config.vm.network :forwarded_port, guest: 443, host: 8443
  config.vm.network :forwarded_port, guest: 8125, host: 8125, protocol: 'tcp'
  config.vm.network :forwarded_port, guest: 8125, host: 8125, protocol: 'udp'
  config.vm.network :forwarded_port, guest: 2003, host: 22003
  config.vm.network :forwarded_port, guest: 2004, host: 22004
  config.vm.network :forwarded_port, guest: 3000, host: 3030
  graphite_version = ENV['GRAPHITE_RELEASE'].nil? ? '1.0.0' : ENV['GRAPHITE_RELEASE']
  config.vm.provision "shell", inline: "cd /vagrant; GRAPHITE_RELEASE=#{graphite_version} ./install"
end
