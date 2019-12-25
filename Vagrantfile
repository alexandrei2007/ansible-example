Vagrant.configure("2") do |config|

    config.vm.define "wordpress" do |wordpress|
        wordpress.vm.box = "ubuntu/bionic64"
        wordpress.vm.network "private_network", ip: "192.168.33.20"
    end

    config.vm.define "mysql" do |mysql|
        mysql.vm.box = "ubuntu/bionic64"
        mysql.vm.network "private_network", ip: "192.168.33.30"
    end
  
  # copiamos as chaves para a pasta "mykeys" por causa da permissão no Windows
  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "ubuntu/bionic64"
    ansible.vm.network "private_network", ip: "192.168.33.10"
    ansible.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update

      sudo apt install software-properties-common -y
      sudo apt-add-repository --yes --update ppa:ansible/ansible
      sudo apt install ansible -y
      sudo apt install python-argcomplete -y
      sudo apt-get install python3-pymysql -y

      sudo mkdir /mykeys
      sudo cp /vagrant/.vagrant/machines/mysql/virtualbox/private_key /mykeys/private_key_mysql
      sudo cp /vagrant/.vagrant/machines/wordpress/virtualbox/private_key /mykeys/private_key_wordpress
      sudo chmod 600 /mykeys/private_key_mysql
      sudo chmod 600 /mykeys/private_key_wordpress
    SHELL
  end
end
