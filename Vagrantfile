Vagrant.configure("2") do |config|
  config.vm.box = "generic/debian12"
  config.vm.hostname = "pj9f4a62-sorosa"
  config.vm.provider "virtualbox" do |v|
    # v.gui = true
    v.name = "pj9f4act62-sorosa"
    v.memory = 3072
    v.cpus = 2
    v.customize ['modifyvm', :id, '--clipboard', 'bidirectional']     
  end

  config.vm.network "public_network"

  config.vm.network "forwarded_port", guest: 80, host: 18000
  #config.vm.network "forwarded_port", guest: 8080, host: 8080
  #config.vm.network "forwarded_port", guest: 8888, host: 8888
  
  config.vm.synced_folder "./projectes", "/home/vagrant/projectes"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update -y
    sudo apt-get install -y net-tools
    sudo apt-get install -y apache2 apache2-doc
    sudo apt-get install -y libapache2-mod-php
    sudo apt-get install -y php8.2 
    sudo apt-get install -y composer php-xml
    mkdir /home/vagrant/pj9f4a6.5
    composer require dompdf/dompdf -d /home/vagrant/pj9f4a6.5
  SHELL
end
