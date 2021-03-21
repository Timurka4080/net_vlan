Vagrant.configure(2) do |config|
    config.vm.box = "centos/7"
  
    config.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "provisioning/playbook.yml"
      ansible.sudo = "true"
    end
  
  
    config.vm.provider "virtualbox" do |v|
        v.memory = 256
    end
  
    config.vm.define "inetrouter" do |inetrouter|
      inetrouter.vm.network "private_network", virtualbox__intnet: "extnet"
      inetrouter.vm.network "private_network", virtualbox__intnet: "extnet"
      inetrouter.vm.hostname = "inetrouter"
    end
  
    config.vm.define "centralrouter" do |centralrouter|
      centralrouter.vm.network "private_network", virtualbox__intnet: "extnet"
      centralrouter.vm.network "private_network", virtualbox__intnet: "extnet"
      centralrouter.vm.network "private_network", ip: "10.10.20.1", virtualbox__intnet: "net1"
      centralrouter.vm.hostname = "centralrouter"
    end
  
    config.vm.define "testserver1" do |testserver1|
      testserver1.vm.network "private_network", ip: "10.10.20.2", virtualbox__intnet: "net1"
      testserver1.vm.hostname = "testserver1"
    end
  
    config.vm.define "testserver2" do |testserver2|
      testserver2.vm.network "private_network", ip: "10.10.20.3", virtualbox__intnet: "net1"
      testserver2.vm.hostname = "testserver2"
    end
  
    config.vm.define "testclient1" do |testclient1|
      testclient1.vm.network "private_network", ip: "10.10.20.3", virtualbox__intnet: "net1"
      testclient1.vm.hostname = "testclient1"
    end
  
    config.vm.define "testclient2" do |testclient2|
      testclient2.vm.network "private_network", ip: "10.10.20.4", virtualbox__intnet: "net1"
      testclient2.vm.hostname = "testclient2"
    end
  end