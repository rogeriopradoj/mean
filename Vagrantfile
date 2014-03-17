# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "chef/ubuntu-13.10"

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provision :shell, :inline => <<-LOCALE
    echo ' # ↑↑↑ locale en_US.UTF-8'

    echo 'LANG="en_US.UTF-8"'     >   /etc/default/locale
    echo 'LANGUAGE="en_US.UTF-8"' >>  /etc/default/locale
    echo 'LC_ALL="en_US.UTF-8"'   >>  /etc/default/locale

LOCALE

  config.vm.provision :shell, :inline => <<-APTGETUPDATE
    echo ' # ↑↑↑ apt get update'

    apt-get -qq update

APTGETUPDATE

  config.vm.provision :shell, :inline => <<-APTGETINSTALL
    echo ' # ↑↑↑ apt get install'

    apt-get -qq -y install build-essential curl wget git vim lynx

APTGETINSTALL

end
