# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 80, host: 8001
  config.vm.network "private_network", ip: "192.168.7.6", netmask: "255.255.255.0"
  config.vm.synced_folder "C:/Users", "/c/Users"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
	vb.cpus = 2
	vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
  end
 
  if Dir.glob("#{File.dirname(__FILE__)}/.vagrant/machines/default/*/id").empty?
    # Install Docker
    pkg_cmd = "wget -q -O - https://get.docker.io/gpg | apt-key add -;" \
      "echo deb http://get.docker.io/ubuntu docker main > /etc/apt/sources.list.d/docker.list;" \
      "apt-get update -qq; apt-get install -q -y --force-yes lxc-docker; "
    # Add vagrant user to the docker group
    pkg_cmd << "usermod -a -G docker vagrant; "
	# Install fig
	pkg_cmd << "curl -L https://github.com/docker/fig/releases/download/1.0.1/fig-`uname -s`-`uname -m` > /usr/local/bin/fig; chmod +x /usr/local/bin/fig"
	
    config.vm.provision :shell, :inline => pkg_cmd
  end
  
end
