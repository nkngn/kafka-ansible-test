Vagrant.configure("2") do |config|
  # Configuration for server1
  config.vm.define "server1" do |server1|
    server1.vm.box = "ubuntu/jammy64"
    server1.vm.network "private_network", ip: "192.168.33.10"
    server1.vm.network "forwarded_port", guest: 22, host: 2230, id: "ssh"
    server1.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 2
    end
    server1.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y docker.io
      sudo usermod -aG docker vagrant
    SHELL
  end

  # Configuration for server2
  config.vm.define "server2" do |server2|
    server2.vm.box = "ubuntu/jammy64"
    server2.vm.network "private_network", ip: "192.168.33.11"
    server2.vm.network "forwarded_port", guest: 22, host: 2231, id: "ssh"
    server2.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 2
    end
    server2.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y docker.io
      sudo usermod -aG docker vagrant
    SHELL
  end

  # Configuration for server3
  config.vm.define "server3" do |server3|
    server3.vm.box = "ubuntu/jammy64"
    server3.vm.network "private_network", ip: "192.168.33.12"
    server3.vm.network "forwarded_port", guest: 22, host: 2232, id: "ssh"
    server3.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 2
    end
    server3.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y docker.io
      sudo usermod -aG docker vagrant
    SHELL
  end
end
