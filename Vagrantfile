# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Online Vagrantfile documentation is at https://docs.vagrantup.com.

  # The AWS provider does not actually need to use a Vagrant box file.
  config.vm.box = "dummy"

  config.vm.provider :aws do |aws, override|
    aws.region = "us-east-1"

    # These options force synchronisation of files to the VM's
    # /vagrant directory using rsync, rather than using trying to use
    # SMB (which will not be available by default).
    override.nfs.functional = false
    override.vm.allowed_synced_folder_types = :rsync

    # AWS CONFIG
    aws.keypair_name = "cosc349labs"
    override.ssh.private_key_path = "~/.ssh/cosc349labs.pem"
    aws.instance_type = "t2.micro"
    aws.security_groups = ["sg-06c74b773a5bdc7db"]
    aws.availability_zone = "us-east-1a"
    aws.subnet_id = "subnet-5395c634"
    aws.ami = "ami-0378588b4ae11ec24"
    override.ssh.username = "ubuntu"
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y apache2
  SHELL
end
