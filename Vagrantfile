$script = <<SCRIPT
sudo apt-get install -qq -y software-properties-common git
sudo apt-add-repository -y ppa:ansible/ansible
sudo apt-get -qq update
sudo apt-get install -qq -y ansible
echo -ne "[defaults]\nroles_path=/opt/ansible_roles\n" > /home/vagrant/.ansible.cfg
sudo mkdir -p /opt/ansible_roles
sudo chown -R vagrant: /opt/ansible_roles
ln -fTs /vagrant /opt/ansible_roles/ansible-role-plex
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "public_network"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end

  config.vm.provision "shell", inline: $script

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "tests/test.yml"
    ansible.install = false
  end
end
