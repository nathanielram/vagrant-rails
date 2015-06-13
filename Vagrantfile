# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  # config.ssh.forward_agent = true

  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network :forwarded_port, guest: 3000, host: 3000

  config.berkshelf.enabled = true

  config.omnibus.chef_version = :latest

  config.vm.provision "shell", path: "fix-libssl.sh"

  config.vm.provision :chef_solo do |chef|
    chef.roles_path = "roles"
    chef.add_role "server"

    chef.json = 
      {
        :rbenv => {
          :rubies => ["2.2.2"],
          :global => "2.2.2",
          :gems => {
            "2.2.2" => [
              {"name" => "bundler"}
            ]
          }
        },
        :postgresql => {
          :users => [
            {
              :username => "vagrant",
              :password => "vagrant",
              :superuser => true,
              :replication => false,
              :createdb => true,
              :createrole => false,
              :inherit => true,
              :login => true
            }
          ],
          :databases => [
            {
              :name => "vagrant",
              :owner => "vagrant",
              :encoding => "UTF-8",
              :locale => "en_US.UTF-8",
            }
          ]
        }
      }
  end    
end
