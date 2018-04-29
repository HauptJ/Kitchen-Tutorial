# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Configure SMB Directory Sharing
  config.vm.synced_folder '.', '/vagrant', {
    type: 'smb', mount_options: ['vers=3.0'],
    smb_username: ENV['VAGRANT_SMB_USERNAME'],
    smb_password: ENV['VAGRANT_SMB_PASSWORD']
  }

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  # Rename if you are builing this box with Packer.
  config.vm.box = "hauptj/CentOS74"
  # Uncomment if you are building this box with Packer.
  # config.vm.box_url = "file://CentOS74.box"
  # Optional if you wish to use root as the default user
  # config.ssh.username = "root"
  # root user SSH password, you can uncomment this if you perfer password authentication
  # config.ssh.password = "vagrant"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #

	config.vm.provider "hyperv" do |hv|
		hv.vmname = "KitchenCI"
		# With nested virtualization, at least 2 CPUs are needed.
		hv.cpus = "4"
		# With nested virtualization, at least 4GB of memory is needed.
		hv.memory = "6144"
	end

  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # Optional, allows you to provision with Ansible locally
    config.vm.provision "shell", inline: <<-SHELL
  #	yum update -y
	# Install Virtualbox
	#wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | rpm --import -
	# Add VirtualBox Repo
	#pushd /etc/yum.repos.d/
	#wget https://download.virtualbox.org/virtualbox/rpm/el/virtualbox.repo
	#popd
	# Install Virtualbox
	#yum install -y VirtualBox-5.2
	# Compile and install kernel headers so Virtualbox works
	#yum install -y gcc kernel-devel
	#sudo /usr/lib/virtualbox/vboxdrv.sh setup
	# Install Vagrant
	#yum install -y https://releases.hashicorp.com/vagrant/2.0.3/vagrant_2.0.3_x86_64.rpm
	# Install Chef DK
	#yum install -y https://packages.chef.io/files/stable/chefdk/2.5.3/el/7/chefdk-2.5.3-1.el7.x86_64.rpm
	# Check Chef DK version
	#chef --version
	# Check Virtualbox version
	#echo 'VirtualBox Version: '
	#VBoxManage --version
	# Check Vagrant version
	#vagrant --version
	# Clone git repository
	#rm -r -f Kitchen-Tutorial/
	#git clone https://github.com/HauptJ/Kitchen-Tutorial.git
	#chown -R vagrant:vagrant Kitchen-Tutorial/
	yum -y upgrade
	yum -y install cifs-utils
    SHELL
end
