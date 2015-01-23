# -*- mode: ruby -*-
# vi: set ft=ruby :
$script = <<SCRIPT
JMETER_VER=2.12

echo "installing java..."
sudo apt-get update
sudo apt-get -y install openjdk-7-jdk

echo "install curl..."
sudo apt-get -y install curl

echo "install jmeter..."
curl -L -O http://mirror.switch.ch/mirror/apache/dist//jmeter/binaries/apache-jmeter-$JMETER_VER.tgz && sudo tar xzf apache-jmeter-$JMETER_VER.tgz -C /opt
sudo mv -f /opt/apache-jmeter-2.12 /opt/jmeter-1 && sudo chown -R vagrant /opt/jmeter-1
sudo cp -Rf /opt/jmeter-1 /opt/jmeter-2
sudo cp -Rf /opt/jmeter-1 /opt/jmeter-3
chown -R vagrant /opt/jmeter-2
chown -R vagrant /opt/jmeter-3
SCRIPT

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_url = "https://vagrantcloud.com/ubuntu/boxes/trusty64"

  config.vm.network "private_network", type: "dhcp"
  config.vm.provision "shell", inline: $script
  config.vm.hostname = "trusty64"

  config.vm.network :forwarded_port, guest: 1099, host: 1099
  config.vm.network :forwarded_port, guest: 1664, host: 1664
  config.vm.network :forwarded_port, guest: 1665, host: 1665

  config.vm.define "rockstar" do |app|
  end

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end

end
