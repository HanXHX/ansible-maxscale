# -*- mode: ruby -*-
# vi: set ft=ruby :
# vi: set tabstop=2 :
# vi: set shiftwidth=2 :

Vagrant.configure("2") do |config|

	vms = [
		["wheezy-upstream-mariadb-master", "deb/wheezy-amd64", "192.168.201.12", ["wheezy","upstream","mariadb","master"]],
		["wheezy-upstream-mariadb-slave", "deb/wheezy-amd64", "192.168.201.13", ["wheezy","upstream","mariadb","slave"]],
		["wheezy-maxscale", "deb/wheezy-amd64", "192.168.201.200", ["maxscale"]]
	]

	config.vm.provider "virtualbox" do |v|
		v.cpus = 1
		v.memory = 256
	end

	vms.each do |vm|
		config.vm.define vm[0] do |m|
			m.vm.box = vm[1]
			m.vm.network "private_network", ip: vm[2]

			m.vm.provision "ansible" do |ansible|
				ansible.playbook = "tests/test.yml"
				if (vm[3].count > 1)
					ansible.groups = {
						vm[3][0] => vm[0],
						vm[3][1] => vm[0],
						vm[3][2] => vm[0],
						vm[3][3] => vm[0],
					}
				else
					ansible.groups = {
						vm[3][0] => vm[0],
					}
				end
				ansible.verbose = 'vv'
				ansible.sudo = true
			end
		end
	end
end
