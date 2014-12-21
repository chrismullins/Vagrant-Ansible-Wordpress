# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.provider :digital_ocean do |provider, override|
    override.ssh.private_key_path = "~/.ssh/private_key"
    override.vm.box = "digital_ocean"
    override.vm.box_url = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"
    provider.token = "alphanumericdigitaloceankey"
    provider.image = "ubuntu-12-04-x64"
    provider.region = "NYC3"
    provider.size = "512mb"
    provider.ssh_key_name = "private_key_name"
  end
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "setup.yml"
    ansible.inventory_path = "vagrant-inventory"
    ansible.host_key_checking = "false"
    ansible.limit = "all"
  end
  config.vm.synced_folder ".", "/vagrant", owner:"www-data", group:"www-data", mount_options:["dmode=775", "fmode=775"]
end
