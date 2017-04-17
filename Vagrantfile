VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.define "vagrant-ansible-test"

  config.vm.network :forwarded_port, guest: 22, host: 9999, id: "ssh"
  config.vm.network "private_network", ip: "192.168.34.10"
  config.vm.hostname = "ansilble.dev"

  config.vm.provider :virtualbox do |vb|
    vb.name = "test-vagrant"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/site.yml"
    ansible.inventory_path = "provisioning/hosts"
    ansible.limit = 'all'
  end
end