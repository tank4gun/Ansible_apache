 
# -*- mode: ruby -*-
# vi: set ft=ruby :

hosts = {
  "host0" => "192.168.33.10",
  "host1" => "192.168.33.11",
}


Vagrant.configure("2") do |config|
  hosts.each do |name, ip|
    config.vm.define name do |machine|
      machine.vm.box = "ubuntu/bionic64"
      machine.vm.hostname = "%s" % name
      machine.vm.network :private_network, ip: ip
      # machine.vm.provider "virtualbox" do |v|
      #    v.name = name
      #    v.customize ["modifyvm", :id, "--memory", 256]
      # end
      machine.vm.provision :ansible do |ansible|
        ansible.playbook = "apache.yml"

        ansible.extra_vars = {
          ansible_python_interpreter: "/usr/bin/python3",
        }
      end
    end
  end
end
