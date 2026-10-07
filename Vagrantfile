IMATGE_BASE = "generic/debian12"
ID = "-sorosa"
BASE_HOSTNAME = "pj9f4a62"
BASE_NAME = "pj9f4act62"
MEMORIA_RAM = 3072
NUM_CPUS = 2
GESTOR_MV = "virtualbox"
TIPUS_XARXA = "public_network"
PORT_GUEST = 80
PORT_HOST = 18000
CARPETA_GUEST = "/home/vagrant/projectes"
CARPETA_HOST = "./projectes"

Vagrant.configure("2") do |config|
  config.vm.box = IMATGE_BASE
  config.vm.hostname = BASE_HOSTNAME + ID
  config.vm.provider GESTOR_MV do |v|
    # v.gui = true
    v.name = BASE_NAME + ID
    v.memory = MEMORIA_RAM
    v.cpus = NUM_CPUS
    v.customize ['modifyvm', :id, '--clipboard', 'bidirectional']     
  end

  config.vm.network TIPUS_XARXA

  config.vm.network "forwarded_port", guest: PORT_GUEST, host: PORT_HOST
  #config.vm.network "forwarded_port", guest: 8080, host: 8080
  #config.vm.network "forwarded_port", guest: 8888, host: 8888
  
  config.vm.synced_folder CARPETA_HOST, CARPETA_GUEST

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