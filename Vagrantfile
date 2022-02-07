Vagrant.configure("2") do |config|

	config.vm.box = "ubuntu/trusty64"

	config.vm.provider "virtualbox" do |vb|
		vb.memory = 1024
	end

	config.vm.define "wordpress" do |wp|
		wp.vm.network "private_network", ip: "172.17.177.41"
	end

	config.vm.define "database" do |db|
		db.vm.network "private_network", ip: "172.17.177.42"
	end

	config.vm.define "ansible" do |ansible|
		ansible.vm.network "private_network",
			ip: "172.17.177.40"
		# Instalando Ansible
		ansible.vm.provision "shell",
			inline: $script_ansible
		ansible.vm.provision "shell",
			inline: $script_wordpress_private_key
		ansible.vm.provision "shell",
			inline: $script_database_private_key
	end

end

$script_ansible = <<-'SCRIPT'
	apt-add-repository -y ppa:ansible/ansible && \
	apt-get update && \
	apt-get install -y software-properties-common && \
	apt-get install -y ansible
SCRIPT

$script_wordpress_private_key = <<-'SCRIPT'
	cp /vagrant/.vagrant/machines/wordpress/virtualbox/private_key /home/vagrant/wordpress_private_key && \
	chmod 600 /home/vagrant/wordpress_private_key && \
	chown vagrant:vagrant /home/vagrant/wordpress_private_key
SCRIPT

$script_database_private_key = <<-'SCRIPT'
	cp /vagrant/.vagrant/machines/database/virtualbox/private_key /home/vagrant/database_private_key && \
	chmod 600 /home/vagrant/database_private_key && \
	chown vagrant:vagrant /home/vagrant/database_private_key
SCRIPT
