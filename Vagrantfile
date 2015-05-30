# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.define "mongodb-master", primary: true do |mongo_db_master|
	mongo_db_master.vm.box = "ubuntu/trusty64"
	mongo_db_master.vm.hostname = "mongodb-master"
	# mongo_db_master.vm.network "forwarded_port", guest: 27017, host: 27017

	mongo_db_master.vm.provision "ansible" do |ansible|
	  ansible.groups = {
		"mongodb-master" => ["mongodb-master"],
	  }
	  ansible.playbook = ".vagrant_lab_playbook.yml"
	  ansible.extra_vars = {
		mongodb_vagrant_develop_env: 'yes',
	  }
	  ansible.sudo = true
	end

	# mongo_db_master.vm.provider :virtualbox do |box|
	#   box.customize ["modifyvm", :id, "--nic2", "intnet", "--intnet2", "mongo-lab"]
	# end
  end

  # config.vm.define "mongodb-slave-01", autostart: false do |sl01|
  #   sl01.vm.box = "ubuntu/trusty64"
  #   sl01.vm.hostname = "mongodb-slave-01"
  #   sl01.vm.provider :virtualbox do |box|
  #     box.customize ["modifyvm", :id, "--nic2", "intnet", "--intnet2", "mongo-lab"]
  #   end
  # end

  # config.vm.define "mongodb-slave-02", autostart: false do |sl02|
  #   sl02.vm.box = "ubuntu/trusty64"
  #   sl02.vm.hostname = "mongodb-slave-01"
  #   sl02.vm.provider :virtualbox do |box|
  #     box.customize ["modifyvm", :id, "--nic2", "intnet", "--intnet2", "mongo-lab"]
  #   end
  # end

end