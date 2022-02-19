Vagrant.configure("2") do |config|
    config.vm.provision "shell", inline: <<-SHELL
        apt-get update -y
	rm /etc/machine-id
	systemd-machine-id-setup
    SHELL
    
    config.vm.define "master" do |master|
      master.vm.box = "mpasternak/focal64-arm"
      master.vm.hostname = "master-node"
      master.vm.provider "parallels" do |vb|
          vb.memory = 1500
          vb.cpus = 1
      end
      master.vm.provision "shell", path: "scripts/common.sh"
      master.vm.provision "shell", path: "scripts/master.sh"
    end

    (1..2).each do |i|
  
    config.vm.define "node0#{i}" do |node|
      node.vm.box = "mpasternak/focal64-arm"
      node.vm.hostname = "worker-node0#{i}"
      node.vm.provider "parallels" do |vb|
          vb.memory = 1500
          vb.cpus = 1
      end
      node.vm.provision "shell", path: "scripts/common.sh"
      node.vm.provision "shell", path: "scripts/node.sh"
    end
    
    end
  end
