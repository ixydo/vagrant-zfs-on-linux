# -*- mode: ruby -*-
# # vi: set ft=ruby :

ENV["LC_ALL"] = "en_US.UTF-8"

Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"
  #config.vm.network :private_network, :ip => '192.168.56.101'
  config.vm.network :private_network, type: "dhcp"

  authorized_keys = `cat ~/.ssh/id_rsa.pub`
  config.vm.provision :shell, :inline => "echo '#{authorized_keys}' >> /home/vagrant/.ssh/authorized_keys"

  config.vm.provider :virtualbox do |v|
    v.memory = 2048
    #v.customize ["modifyvm", :id, "--firmware", "efi"]

    for vol in ['1', '2', '3', '4', '5'] do
      disk_file = File.absolute_path("./.vboxhdd/disk#{vol}.vdi")

      if not File.exists?(disk_file)
        v.customize [
            'createhd',
            '--filename', disk_file,
            '--size', 2048
        ]
        v.customize [
            'storageattach', :id,
            '--storagectl', 'SATA Controller',
            '--port', vol,
            '--device', 0,
            '--type', 'hdd',
            '--medium', disk_file
        ]
      end
    end
  end

  #config.vm.provision :shell, :inline => "sudo /bin/bash /vagrant/bootstrap"
end
