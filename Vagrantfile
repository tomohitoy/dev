VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "centos67"
    config.vm.network :private_network, ip: "192.168.33.10"
    config.vm.network :forwarded_port, guest: 3000, host: 3000
    config.ssh.insert_key = false
    config.vm.provision :ansible do |ansible|
      ansible.playbook = "provision/playbook_vagrant.yml"
      ansible.inventory_path = "provision/dev_hosts"
      ansible.limit = 'all'
      ansible.verbose = 'vvv'
    end
end
