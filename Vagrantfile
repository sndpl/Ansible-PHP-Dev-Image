VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config_values = {
    memory: 512,
    name: "phpansible",
    ip: "33.33.33.61"
  }

  # Overwrites config_values
  if File.exists? 'Vagrantfile.local'
    eval File.read 'Vagrantfile.local'
  end

  config.vm.box = "debian71-64"
  config.vm.box_url = "https://dl.dropboxusercontent.com/u/197673519/debian-7.2.0.box"

  config.vm.network :private_network, ip: config_values[:ip]

  config.ssh.forward_agent = true

  config.vm.synced_folder "./", "/var/www/phpansible.dev", id: "vagrant-root", :nfs => true
  config.vm.synced_folder "/www/composer", "/var/www/composer", id: "vagrant-root", :nfs => true

  config.vm.provider :virtualbox do |vb|
    vb.customize [
       "modifyvm", :id,
       "--name", config_values[:name],
       "--memory", config_values[:memory],
       "--natdnshostresolver1", "on"
    ]
  end

  config.vm.provision :ansible do |ansible|
     ansible.playbook = "provisioning/playbook.yml"
     #ansible.verbose = "v"
     ansible.extra_vars = {
        private_interface: config_values[:ip],
        hostname: config_values[:name]
        }
  end
end
