VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  # Vagrant Cacher
  # see: http://qiita.com/succi0303/items/e06bca7db5a0c3de96af#3-2
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end

  config.vm.define "vagrant-ansible-test" do |vansible|
    vansible.vm.network :forwarded_port, guest: 22, host: 9999, id: "ssh"
    vansible.vm.network "private_network", ip: "192.168.34.10"
    vansible.vm.hostname = "ansilble.dev"

    vansible.vm.provider :virtualbox do |vb|
      vb.name = "test-vagrant"
    end

    vansible.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/site.yml"
      ansible.inventory_path = "provisioning/hosts"
      ansible.limit = 'all'
    end
  end

end