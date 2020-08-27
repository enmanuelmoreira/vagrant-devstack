Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.disksize.size = "70GB"
  config.vm.hostname = "openstack-controller"
  config.vm.network "public_network", bridge: "enp8s0"
  config.vm.provider "virtualbox" do |v|
    v.memory = 10240
    v.cpus = 8
    v.name = "openstack-controller"
  end
  config.vm.provision "shell", path: "initial-devstack-setup.sh"
end