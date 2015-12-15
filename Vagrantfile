# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "1432"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-i386-vagrant-disk1.box"

  config.vm.network :private_network, ip: "2.2.2.2"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--name", "Meansible", "--memory", "512"]
    # Display the VirtualBox GUI when booting the machine
    vb.gui = false
  end

# Shared folder from the host machine to the guest machine.
  config.vm.synced_folder "../../mean/", "/webapps/ansible/"
  
  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "vagrant.yml"
    ansible.host_key_checking = false
    ansible.verbose = "v"
  end

  config.ssh.forward_agent = true

#config.vm.provision :shell, :inline => "sudo supervisorctl restart djansible"
end
