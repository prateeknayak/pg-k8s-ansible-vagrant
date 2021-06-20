Vagrant.require_version ">= 1.7.0"

IMAGE_NAME = "bento/ubuntu-20.10"
N = 2

# this makes it bit brittle but meh
$script = <<-'SCRIPT'
echo "192.168.50.10 k8s-m1" | tee -a /etc/hosts
echo "192.168.50.11 k8s-n1" | tee -a /etc/hosts
echo "192.168.50.12 k8s-n2" | tee -a /etc/hosts
SCRIPT

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 2
        v.gui = false
    end
      
    config.vm.define "k8s-m1" do |master|
        master.vm.box = IMAGE_NAME
        master.vm.network "private_network", ip: "192.168.50.10"
        master.vm.hostname = "k8s-m1"
        master.vm.provision "shell", inline: $script
    end

    (1..N).each do |i|
        config.vm.define "k8s-n#{i}" do |node|
            node.vm.box = IMAGE_NAME
            node.vm.network "private_network", ip: "192.168.50.#{i + 10}"
            node.vm.hostname = "k8s-n#{i}"
            node.vm.provision "shell", inline: $script
        end
    end
end
