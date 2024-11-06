Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/bionic64"
  
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    config.vm.network "forwarded_port", guest: 80, host: 8080

    config.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install -y apache2
      sudo systemctl start apache2
      sudo systemctl enable apache2
    SHELL

    config.vm.synced_folder "./web", "/var/www/html"
  end