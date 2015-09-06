# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|

    config.vm.define :node1 do |node|
    node.vm.box = "cent6.4"
    node.vm.network :forwarded_port, guest: 22, host: 2001, id: "ssh"
    node.vm.network :public_network, ip: "192.168.11.50"
    node.vm.hostname = "andromeda.usamintech"
    node.vm.provision "shell", inline: <<-SHELL
      sudo yum install -y python
      sudo rpm -ivh http://ftp.riken.jp/Linux/fedora/epel/6/i386/epel-release-6-8.noarch.rpm
      sudo yum install -y ansible
      cd
      echo 192.168.11.51 > hosts
    SHELL
  end

  config.vm.define :node2 do |node|
    node.vm.box = "cent6.4"
    node.vm.network :forwarded_port, guest: 22, host: 2002, id: "ssh"
    node.vm.network :forwarded_port, guest: 80, host: 8000, id: "http"
    node.vm.network :public_network, ip: "192.168.11.51"
    node.vm.hostname = "delphinus.usamintech"
    node.vm.provision "shell", inline: <<-SHELL
      sudo yum update -y
      sudo rpm -ivh http://ftp.riken.jp/Linux/fedora/epel/6/i386/epel-release-6-8.noarch.rpm
      sudo yum install -y ansible
      # 
      
    SHELL
  end 
  
  # config.vm.box = "cent6.4"
  # config.vm.network "public_network" ,ip: "192.168.11.9"

end
