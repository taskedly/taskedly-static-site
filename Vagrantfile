# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.4"

  #config.vm.synced_folder "ansible/", "/vagrant"
  #config.vm.synced_folder "docker/", "/vagrant"
  #config.vm.synced_folder "src/", "/vagrant"


  config.vm.define "app1" do |server|
    server.vm.hostname = "server.example.com"
    server.vm.network :private_network, ip: "192.168.60.4"
  end

  # Run Ansible from the Vagrant VM
  config.vm.provision "ansible_local" do |ansible|
    ansible.become = true
    ansible.playbook = "ansible/playbook.yml"
    ansible.galaxy_role_file = "ansible/requirements.yml"
    ansible.galaxy_roles_path = "/etc/ansible/roles"
    ansible.galaxy_command = "sudo ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path} --force"
    ansible.verbose = true
  end

end
