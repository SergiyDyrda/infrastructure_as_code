
$installansible = <<SCRIPT
sudo apt-get update
sudo apt-get install -y software-properties-common 
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install -y ansible
SCRIPT

$sudovagrant = <<SCRIPT
usermod -aG sudo vagrant
SCRIPT

Vagrant.configure("2") do |config|

 config.vm.provider "virtualbox" do |v|
    v.linked_clone = true
    v.customize ["modifyvm", :id, "--memory", "512", "--cpus", "1"]
 end

 config.vm.define "manager" do |mg|
   mg.vm.box = "ubuntu/trusty64"
   mg.vm.hostname = "manager"
   mg.vm.network :private_network, ip: "192.168.10.3"
   mg.vm.provision "file", source: "project", destination: "$HOME/project"
   mg.vm.provision "shell", inline: $sudovagrant
 end
 
 config.vm.define "nginx-server" do |nx|
   nx.vm.box = "ubuntu/trusty64"
   nx.vm.hostname = "nginx"
   nx.vm.network :private_network, ip: "192.168.10.10"
   nx.vm.provision "shell", inline: $sudovagrant
 end

 config.vm.define "server-1" do |s1|
   s1.vm.box = "ubuntu/trusty64"
   s1.vm.hostname = "server-1"
   s1.vm.network :private_network, ip: "192.168.10.20"
   s1.vm.provision "shell", inline: $sudovagrant 
 end

 config.vm.define "server-2" do |s2|
   s2.vm.box = "ubuntu/trusty64"
   s2.vm.hostname = "server-2"
   s2.vm.network :private_network, ip: "192.168.10.30"
   s2.vm.provision "shell", inline: $sudovagrant 
 end

 config.vm.define "database" do |db|
   db.vm.box = "ubuntu/trusty64"
   db.vm.hostname = "database"
   db.vm.network :private_network, ip: "192.168.10.40"
   db.vm.provision "shell", inline: $sudovagrant 
 end

end
