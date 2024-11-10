Vagrant.configure("2") do |config|
  # Caja base de Ubuntu 18.04
  config.vm.box = "ubuntu/bionic64"

  # Configuración del proveedor de VirtualBox (en este caso, la VM se ejecutará en VirtualBox)
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"  # Configura 512 MB de RAM
    vb.cpus = 1        # Configura 1 CPU
  end

  # Red privada (opcional si necesitas asignar una IP fija)
  config.vm.network "private_network", type: "dhcp"

  # Carpeta compartida: Usa una ruta absoluta para evitar problemas con rutas relativas
  config.vm.synced_folder "C:/paginas_web", "/var/www/html"

  # Provisionamiento: Instala Apache en la VM
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    sudo systemctl enable apache2
    sudo systemctl start apache2
  SHELL
end
