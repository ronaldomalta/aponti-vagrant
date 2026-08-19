Vagrant.configure("2") do |config|

  
  config.vm.box = "ubuntu/jammy64"

  
  config.vm.provider "virtualbox" do |vb|
    vb.name = "aponti-dev"
    vb.memory = "2048"
    vb.cpus = 2
  end

  

  
  config.vm.network "forwarded_port",
    guest: 8080,
    host: 8080

  
  config.vm.network "forwarded_port",
    guest: 3000,
    host: 3000

  
  config.vm.network "forwarded_port",
    guest: 5432,
    host: 5432

  
  config.vm.network "private_network",
    ip: "192.168.56.10"

  
  config.vm.synced_folder ".", "/projeto"

 
  config.vm.provision "shell", inline: <<-SHELL

    
    sudo apt-get update

    
    sudo apt-get install -y curl git unzip ca-certificates

    
    curl -fsSL https://get.docker.com -o get-docker.sh
    sudo sh get-docker.sh

    
    sudo usermod -aG docker vagrant

    sudo apt-get install -y docker-compose-plugin

    sudo systemctl enable docker
    sudo systemctl start docker

  SHELL

end