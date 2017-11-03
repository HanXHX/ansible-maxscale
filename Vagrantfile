# -*- mode: ruby -*-
# vi: set ft=ruby :
# vi: set tabstop=2 :
# vi: set shiftwidth=2 :

Vagrant.configure("2") do |config|

  vms = [
    { :name => "debian-jessie-sysvinit",  :box => "debian/jessie64", :vars => {"__init" => "sysvinit" }},
    { :name => "debian-jessie-systemd",   :box => "debian/jessie64", :vars => {"__init" => "systemd"}},
    { :name => "debian-stretch-sysvinit", :box => "debian/stretch64", :vars => {"__init" => "sysvinit" }},
    { :name => "debian-stretch-systemd",  :box => "debian/stretch64", :vars => {"__init" => "systemd"}}
  ]

  conts = [
    { :name => "docker-debian-jessie",  :docker => "hanxhx/vagrant-ansible:debian8", :vars => { "__init" => "systemd" }},
    { :name => "docker-debian-stretch", :docker => "hanxhx/vagrant-ansible:debian9", :vars => { "__init" => "systemd" }}
  ]

  config.vm.network "private_network", type: "dhcp"

  conts.each do |opts|
    config.vm.define opts[:name] do |m|
      m.vm.provider "docker" do |d|
        d.image = opts[:docker]
        d.remains_running = true
        d.has_ssh = true
      end
      m.vm.provision "ansible" do |ansible|
        ansible.playbook = "tests/test.yml"
        ansible.verbose = 'vv'
        ansible.sudo = true
        ansible.extra_vars = opts[:vars]
      end
    end
  end

  vms.each do |opts|
    config.vm.define opts[:name] do |m|
      m.vm.box = opts[:box]
      m.vm.provider "virtualbox" do |v|
        v.cpus = 1
        v.memory = 256
      end
       m.vm.provision "ansible" do |ansible|
         ansible.playbook = "tests/test.yml"
         ansible.verbose = 'vv'
         ansible.sudo = true
         ansible.extra_vars = opts[:vars]
       end
    end
  end



end
