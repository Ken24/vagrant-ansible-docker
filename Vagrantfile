Vagrant.configure(2) do |config|
  config.vm.box = "bento/centos-7.2"
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "512"
    vb.cpus = 1
  end

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box  
  end

  config.vm.define "mgmt" do |db|
    db.vm.network :private_network, ip: "192.168.33.41"
  end
  config.vm.define "dc01" do |ap|
    ap.vm.network :private_network, ip: "192.168.33.42"
  end
  config.vm.define "dc02" do |wb|
    wb.vm.network :private_network, ip: "192.168.33.43"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "pb-docker.yml"
  end
end
