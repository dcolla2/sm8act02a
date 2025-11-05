Vagrant.configure("2") do |config|
	config.vm.box = "debian/bookworm64"
	config.vm.hostname = "daw2.fjeclot.local"
  
	config.vm.provider "virtualbox" do |v|
		v.name = "daw2"
		v.memory = 2048
		v.cpus = 2
		v.customize ['modifyvm', :id, '--clipboard', 'bidirectional']     
	end
  
	config.vm.network "public_network"
         
	config.vm.synced_folder "./codis", "/var/www/html", owner: "www-data", group: "www-data"
    
	config.vm.provision "shell", inline: <<-SHELL
		sudo apt-get update -y
		sudo apt-get install -y aptitude
		sudo apt-get install -y net-tools
		sudo apt-get install -y git
		sudo apt-get install -y nano
		sudo apt-get install -y apache2 apache2-doc
		sudo apt-get install -y libapache2-mod-php
		sudo apt-get install -y php8.2
		sudo aptitude install -y php-xml composer
		sudo gpasswd -a vagrant www-data
		sudo chmod -R 770 /var/www/html		
		exit    
	SHELL

end
