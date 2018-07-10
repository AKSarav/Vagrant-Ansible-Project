# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |test|
 test.vm.box_check_update = "false"
 test.vm.provider "virtualbox" do |vb|
   vb.memory = "1024"
 end
 
 test.vm.define "webserver" do |web|
   web.vm.hostname = "mwiws01"
   web.vm.box = "geerlingguy/centos7"
   web.vm.network :private_network, ip: "192.168.10.10"
   web.vm.network "forwarded_port", guest: "80", host: "8080"
   web.vm.synced_folder "/apps/shared", "/shared"
   
   #Provision the webserver with Ansible
   web.vm.provision "ansible" do |ansible|
     ansible.playbook="apache-playbook.yaml"
   end
 end
end
