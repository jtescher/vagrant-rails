# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  # Use ubuntu base
  config.vm.box = "ubuntu/trusty64"

  # Forward Rails port
  config.vm.network "forwarded_port", guest: 3000, host: 3000

  # Configure chef recipes
  config.vm.provision :chef_zero do |chef|
    chef.json = {
      'postgresql' => {
        'password'  => {
          'postgres' => 'iloverandompasswordsbutthiswilldo'
        }
      }
    }
    chef.run_list = [
      # Install Ruby
      "recipe[ruby-ng::dev]",

      # Install Node.js for rails assets
      "recipe[nodejs::default]",

      # Install PostgreSQL DB
      "recipe[postgresql::server]"
    ]
  end

end
