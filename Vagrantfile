Vagrant.configure(2) do |config|
  config.vm.provider :virtualbox do |vb|
    vb.name = "crystal"
  end

  config.vm.network :private_network, ip: "172.16.33.123"
  config.vm.box = "AntonioMeireles/coreos-stable"
  config.vm.provision "shell", inline: <<-EOS
docker pull manastech/crystal
  EOS
end
