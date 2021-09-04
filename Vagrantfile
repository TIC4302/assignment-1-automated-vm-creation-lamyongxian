Vagrant.configure("2") do |config|

    config.vm.define "attacker" do |attacker|
        attacker.vm.box = "kalilinux/rolling"

        attacker.vm.network "private_network", type: "dhcp"
        attacker.vm.network "private_network", ip: "192.168.1.2", virtualbox__intnet: true

        attacker.vm.provider "virtualbox" do |vb_attacker|
            vb_attacker.memory = 1024
            vb_attacker.cpus = 2
            vb_attacker.gui = true
        end
        
        # Prevent SharedFoldersEnableSymlinksCreate errors
        attacker.vm.synced_folder ".", "/vagrant", disabled: true
    end

    config.vm.define "victim" do |victim|
        victim.vm.box = "generic/ubuntu1804"

        #victim.vm.define 'ubuntu'

        victim.vm.network "private_network", type: "dhcp"
        victim.vm.network "private_network", ip: "192.168.1.10", virtualbox__intnet: true

        victim.vm.provider "virtualbox" do |vb_victim|
            vb_victim.memory = 1024
            vb_victim.cpus = 2
            vb_victim.gui = true
        end

        # Prevent SharedFoldersEnableSymlinksCreate errors
        victim.vm.synced_folder ".", "/vagrant", disabled: true
    end
end
