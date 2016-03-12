# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "boxcutter/centos71"
  config.vm.hostname = "docker"
  config.vm.box_check_update = false

  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Add the required puppet modules before provisioning is run by puppet
  config.vm.provision :shell do |shell|
      shell.inline = "yum install -y epel-release ;
                      yum install -y puppet ;
                      puppet module install puppetlabs-stdlib;
                      puppet module install puppetlabs-apt;
                      puppet module install stahnma/epel;
                      puppet module install garethr-docker;
                      touch /etc/puppet/hiera.yaml
                      exit 0"
  end

  # Use Puppet to provision the server and setup an elastic search cluster
  # on a single box
  config.vm.provision "puppet" do |puppet|
  end
end
