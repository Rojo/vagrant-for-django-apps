# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = 'ubuntu/xenial64'
  config.vm.define "prescript"

  # Port forwarding
  [
    8000 # Django
  ].each do |p|
    config.vm.network :forwarded_port, guest: p, host: p
  end

  # Provider configuration
  config.vm.provider 'virtualbox' do |vb|
    vb.customize ['modifyvm', :id, '--memory', '1024']
  end

  # Sync folders
  config.vm.synced_folder '.', '/vagrant', type: 'virtualbox'

  # Machine initial provision
  config.vm.provision "shell", privileged: false, run: "once",
  path: "provision/box_setup.ssh",
  env: {
    "LC_ALL"   => "en_US.UTF-8",
    "LANG"     => "en_US.UTF-8",
    "LANGUAGE" => "en_US.UTF-8",
  }
end
