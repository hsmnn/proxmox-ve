Vagrant.configure("2") do |config|
    config.vm.box = "output/proxmox-ve-amd64-virtualbox.box"
    config.vm.box_version = "6.1"

    config.vm.hostname = "proxmox-node"
    config.vm.network "forwarded_port", guest: 8006, host: 8006, auto_correct: true
    config.vm.provider :virtualbox do |vb|
            vb.name = "proxmox-node"
    end
end