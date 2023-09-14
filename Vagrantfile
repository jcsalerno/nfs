Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/bionic64"
    config.vm.network "private_network", ip: "172.89.0.20"
  
    config.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get upgrade -y
      mkdir -p /srv/wordpress
      apt install nfs-kernel-server apache2 -y
      systemctl stop apache2
      systemctl disable apache2
      chmod 755 /srv/wordpress
      chown www-data:www-data /srv/wordpress
      echo '/srv/wordpress 172.89.0.0/24(rw,no_subtree_check,no_root_squash)' > /etc/exports
      exportfs -rva
    SHELL
  
  end