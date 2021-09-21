Vagrant.configure("2") do |config|
config.vm.boot_timeout = 600

  config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 1
  end

  config.vm.provision "file", source: "key/id_rsa.pub", destination: "/home/vagrant/.ssh/id_rsa.pub"
  config.vm.provision "shell", inline: <<-SHELL
    cat /home/vagrant/.ssh/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys
  SHELL

  config.vm.define "proxysql" do |proxysql|
    proxysql.vm.box = "ubuntu/focal64"
    proxysql.vm.hostname = "proxysql"
    proxysql.vm.network "private_network", ip: "192.168.4.2", hostname: true
    proxysql.vm.network "private_network", ip: "192.168.6.2", hostname: true
    proxysql.vm.synced_folder ".", "/vagrant", disabled: true
  end

  config.vm.define "pxc1" do |pxc1|
    pxc1.vm.box = "ubuntu/focal64"
    pxc1.vm.hostname = "pxc1"
    pxc1.vm.network "private_network", ip: "192.168.6.3", hostname: true
    pxc1.vm.synced_folder ".", "/vagrant", disabled: true
  end

  config.vm.define "pxc2" do |pxc2|
    pxc2.vm.box = "ubuntu/focal64"
    pxc2.vm.hostname = "pxc2"
    pxc2.vm.network "private_network", ip: "192.168.6.4", hostname: true
    pxc2.vm.synced_folder ".", "/vagrant", disabled: true
  end

  config.vm.define "pxc3" do |pxc3|
    pxc3.vm.box = "ubuntu/focal64"
    pxc3.vm.hostname = "pxc3"
    pxc3.vm.network "private_network", ip: "192.168.6.5", hostname: true
    pxc3.vm.synced_folder ".", "/vagrant", disabled: true
  end

end
