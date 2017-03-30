# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.hostname = "ansible-control-mach1"
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "public_network", ip: "192.168.0.149" , bridge: "Realtek PCIe FE Family Controller"
    config.ssh.forward_agent    = true
    config.ssh.insert_key       = false
    config.ssh.private_key_path =  ["~/.vagrant.d/insecure_private_key","id_rsa1"]
    ssh_pub_key = File.readlines("id_rsa1.pub").first.strip
    config.vm.provision :shell, privileged: false,  inline: <<-SCRIPT
    sudo chmod ugo+x /vagrant/runonce.sh 
    sudo /bin/bash /vagrant/runonce.sh "#{ssh_pub_key}"
    SCRIPT
	config.vm.provider "virtualbox" do |v|
		v.memory = 1024
		v.cpus = 2
	 end

end
