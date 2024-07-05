# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Box (base image)
  config.vm.box = "ubuntu/bionic64"

  # VM settings
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = 2
  end

  # Hostname and Network settings
  config.vm.hostname = "nginx-flask-compose-vagrant"
  config.vm.network "public_network", type: "dhcp"

  # Shell provisioning
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y \
      apt-transport-https \
      ca-certificates \
      curl \
      gnupg-agent \
      software-properties-common \
      git
    
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

    # Docker and Docker Compose install
    apt-get update
    apt-get install -y docker-ce docker-ce-cli containerd.io

    curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose
    
    git clone https://github.com/canogluonur/flask-vagrant.git /home/vagrant/flask-vagrant
    cd /home/vagrant/flask-vagrant
    docker-compose up -d --build
  SHELL
end
