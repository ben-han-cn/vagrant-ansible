Vagrant.configure(2) do |config|
  config.vm.box_check_update = false
  config.vm.box = "ubuntu/trusty64"
  config.vm.network :forwarded_port, guest: 22, host: 8999, id: "ssh"
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
    v.gui = false
    v.customize ["modifyvm", :id, "--name", "goenv"]
  end

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.host_key_checking = false
    ansible.verbose = "vvv"
  end
end
