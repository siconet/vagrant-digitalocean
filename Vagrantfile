# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # sets the hostname
  config.vm.hostname = '{{APP_NAME}}'

  config.vm.box = "digital_ocean"
  #config.vm.synced_folder "..", "/{{APP_NAME}}"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.limit = 'all'
  end

  config.ssh.private_key_path = "./id_rsa_vagrant"
  config.vm.provider :digital_ocean do |provider|
    provider.ssh_key_name = "{{DIGITAL_OCEAN_KEY_NAME}}"
    provider.token = "{{DIGITAL_OCEAN_PROVIDER_TOKEN}}"
    provider.image = 'ubuntu-14-10-x64'
    provider.region = 'ams1'
    provider.size = '512mb'
  end
end