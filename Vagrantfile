Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = "1024"
    v.cpus = 2
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "70"]
  end
  config.vm.define :mongodb do |server|
    server.vm.box = "clouddood/RH7.5_baserepo"
    server.vm.host_name = "mongodb"

    server.ssh.forward_agent = true

    server.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_mongodb.yml"
      ansible.inventory_path = "vagrant_hosts"
#     ansible.tags = ansible_tags
#     ansible.verbose = ansible_verbosity
#     ansible.extra_vars = ansible_extra_vars
#     ansible.limit = ansible_limit
    end

#   server.vm.network :private_network, ip: "10.0.1.26"
    server.vm.network :private_network, ip: "192.168.60.99"
  end
end


