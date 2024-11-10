# Vagrantfile para un servidor con Apache en el puerto 8080
Vagrant.configure("2") do |config|
    # Especifica la caja base
    config.vm.box = "ubuntu/jammy64" # Puedes cambiar esta caja por otra si lo prefieres
  
    # Configura la máquina virtual
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 2
    end
  
    # Configura el hostname
    config.vm.hostname = "servidor-apache"
  
    # Reenvía el puerto 8080 del host al puerto 80 de la VM
    config.vm.network "forwarded_port", guest: 80, host: 8080
  
    # Sincroniza el directorio local con el directorio de Apache en la VM
    config.vm.synced_folder "./html", "/var/www/html"
  
    # Provisiona la VM para instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      systemctl enable apache2
      systemctl start apache2
    SHELL
  end
   