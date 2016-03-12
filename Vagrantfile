# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "debian/jessie64"
  config.vm.box_check_update = true

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "1024"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "gitlab-runner.yml"
    ansible.extra_vars = {
      ci_auth_token: ""
    }
  end
end
