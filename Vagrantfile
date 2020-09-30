# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config| 
  config.vm.box = "base"

  config.vm.define "centos" do |centosvm| 	
  	centosvm.vm.box = "centos/7"
  end

  config.vm.define "dns" do |dnsvm| 	
  	dnsvm.vm.box = "centos/7"
	dnsvm.vm.network "public_network", bridge: "wifi0"
	dnsvm.vm.hostname = "dnsserver"
	dnsvm.vm.provision "shell", inline: "sudo yum install -y bind bind-utils"
 	dnsvm.vm.provision "shell", inline: "sudo systemctl start named && sudo systemctl enable named"
	dnsvm.vm.provider "virtualbox" do |vb|
		vb.memory = 300
		vb.cpus = 1	
		vb.name	= "dns-server"
	end
 end
  
  config.vm.define "ubuntu" do |ubuntuvm|
    ubuntuvm.vm.box = "ubuntu/bionic64"
    ubuntuvm.vm.network "public_network", bridge: "wifi0" 
  end
end
