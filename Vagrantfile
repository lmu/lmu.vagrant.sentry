# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "canonical/trusty64"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"

  config.vm.define "sentry1", primary: true do |sentry|
    sentry.vm.provider "virtualbox" do |vb|
      vb.name = "Sentry-APP1"
      vb.memory = 8192
      vb.cpus = 8
      #vb.synced_folder "./shared_folders/server.sentry/data", "/data", owner: "root", group: "root"
    end
    sentry.vm.network :private_network, ip: "192.168.1.90"
  end

  config.vm.provision "ansible" do |ansible|
    # Ansible Playbook
    ansible.limit = "all"
    ansible.playbook = "lmu.ansible.playbooks/base-preseed.yml"
  end

end
