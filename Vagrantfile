# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.hostname = "jenkins.dev"
  config.vm.network :forwarded_port, guest: 8080, host: 8080
  config.vm.network :private_network, ip: "192.168.33.11"

  config.vm.provision :shell, :inline => "gem install chef --version 11.4.2 --no-rdoc --no-ri --conservative"
  config.vm.provision :shell, :inline => "apt-get update"

  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
  #
  config.vm.provision :chef_solo do |chef|

    chef.cookbooks_path = "cookbooks"
    chef.add_recipe("java")
    chef.add_recipe("ant")
    chef.add_recipe("maven")
    chef.add_recipe("git")
    chef.add_recipe("jenkins::server")

  end
end
