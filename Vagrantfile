# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # sets the hostname
  config.vm.hostname = 'example.dev'
  
  config.vm.box = "digital_ocean"
  #config.vm.define = "example.dev"
  config.vm.synced_folder "..", "/example.dev"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.limit = 'all'
  end

  config.ssh.private_key_path = "./id_rsa_vagrant"
  config.vm.provider :digital_ocean do |provider|
    provider.token = "{{PROVIDER_TOKEN}}"
    provider.image = 'ubuntu-14-10-x64'
    provider.region = 'ams1'
    provider.size = '512mb'
  end
end