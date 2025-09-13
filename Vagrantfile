Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-24.04"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo timedatectl set-timezone Europe/Moscow
    echo "alias cls='clear'" >> /home/vagrant/.bashrc
    echo "alias cls='clear'" >> /root/.bashrc
  SHELL
  
  config.vm.define "docker" do |docker|
      docker.vm.hostname = "docker"
      docker.vm.network "private_network", ip: "192.168.56.4"
      docker.vm.network "forwarded_port", guest: 8000, host: 8000, auto_correct: true
    
  end

end