# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.ssh.forward_x11 = true
  config.vm.synced_folder 'nzbDrone', '/home/vagrant/nzbDrone',  owner: 'vagrant', group: 'vagrant'
  

  config.vm.provision :ansible do |ansible|
      ansible.playbook = 'transmission.yml'
      ansible.sudo = true
      ansible.groups = {
          'all' => ['default'],
          'all:vars' => {
              'pia_user' => ENV.fetch('PIA_USER'),
              'pia_pass' => ENV.fetch('PIA_PASS'),
          }
      }
  end
end
