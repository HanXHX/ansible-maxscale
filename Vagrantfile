# -*- mode: ruby -*-
# vi: set ft=ruby :
# vi: set tabstop=2 :
# vi: set shiftwidth=2 :

Vagrant.configure("2") do |config|

	vms = [
		{ :name => "jessie-maxscale-sysvinit", :box => "debian/jessie64", :vars => {"__init" => "sysvinit" }},
		{ :name => "jessie-maxscale-systemd",  :box => "debian/jessie64", :vars => {"__init" => "systemd"}}
	]

	config.vm.provider "virtualbox" do |v|
		v.cpus = 1
		v.memory = 256
	end

	config.vm.synced_folder ".", "/vagrant", disabled: true

	vms.each do |vm|
		config.vm.define vm[:name] do |m|
			m.vm.box = vm[:box]
			m.vm.network "private_network", type: "dhcp"

			m.vm.provision "ansible" do |ansible|
				ansible.playbook = "tests/test.yml"
				ansible.verbose = 'vv'
				ansible.sudo = true
				ansible.extra_vars = vm[:vars]
			end
		end
	end
end
