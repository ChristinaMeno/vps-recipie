# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.hostname = 'black-kite'
  config.ssh.username = 'freebsd'
  config.vm.synced_folder ".", "/home/freebsd/vagrant", type: "nfs"
  config.ssh.shell = 'tcsh'

  config.vm.provider :digital_ocean do |provider, override|
    override.ssh.private_key_path = '~/.ssh/id_rsa'
    override.vm.box = 'digital_ocean'
    override.vm.box_url = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"
    provider.token = ENV['DIGITAL_OCEAN_API_TOKEN']
    provider.image = 'freebsd-10-2-x64'
    provider.region = 'sfo1'
    provider.size = '512mb'
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end

end
