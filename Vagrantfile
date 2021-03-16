Vagrant.configure("2") do |config|
  # не копировать приват ключ в хостовую машину dd
  # изменить объем памяти для виртуальной машины по умолчанию
   config.vm.provider :virtualbox do |vb|
     config.ssh.insert_key = false
     vb.customize ["modifyvm", :id, "--memory", "2048"]
     config.vm.synced_folder "./", "/vagrant", disabled: true
   end

  # Node 1 Hybris
  config.vm.define "main_server" do |main_server|
    main_server.vm.hostname = "hybris-node-1"
    main_server.vm.box = "geerlingguy/ubuntu1804"
    main_server.vm.network :private_network, ip: "192.168.12.4" #, virtualbox__intnet: "mynetwork"
    #  main_server.vm.network "forwarded_port", guest: 8080, host: 8087, host_ip: "127.0.0.1", guest_ip: "192.168.150.4"
    # main_server.vm.network "forwarded_port", guest: 7777, host: 7777, host_ip: "127.0.0.1", guest_ip: "192.168.150.4"
    main_server.vm.provision "ansible" do |ansible| #fd
        ansible.verbose = "v"
        ansible.playbook = "./provision/ansible/main-playbook.yml"
    end
  end
  # Node 2 Hybris
    config.vm.define "node" do |node|
      node.vm.hostname = "hybris-node-2"
      node.vm.box = "geerlingguy/ubuntu1804"
      node.vm.network :private_network, ip: "192.168.12.5" #, virtualbox__intnet: "mynetwork"
      #  main_server.vm.network "forwarded_port", guest: 8080, host: 8087, host_ip: "127.0.0.1", guest_ip: "192.168.150.4"
      # main_server.vm.network "forwarded_port", guest: 7777, host: 7777, host_ip: "127.0.0.1", guest_ip: "192.168.150.4"
      node.vm.provision "ansible" do |ansible| #fd
          ansible.verbose = "v"
          ansible.playbook = "./provision/ansible/main-playbook.yml"
      end
    end


end
