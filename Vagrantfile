Vagrant.configure("2") do |config|
    OpenstackNodes = 5
    (2..OpenstackNodes).each do |i|
      config.vm.define "ubuntu-osa#{i}" do |controller|
        controller.vm.box = "generic/ubuntu2004"
        controller.vm.hostname = "controller#{i}"
        ### MGMt Net  ###
        controller.vm.network "private_network", ip: "172.16.16.#{i}"
        ### Vxlan Net ###
        controller.vm.network "private_network", ip: "172.16.17.#{i}"
        ### Storage Net ### 
        controller.vm.network "private_network", ip: "172.16.18.#{i}"
        controller.vm.provider :libvirt do |v|
          v.memory  = 4096
          v.cpus    = 2
        end
      end
    end  
      config.vm.define "ubuntu-osa-bastion" do | bastion |
        bastion.vm.box = "generic/ubuntu2004"
        bastion.vm.network "private_network", ip: "172.16.16.11"
      end
      config.vm.define "log-host" do | log |
        log.vm.box = "generic/ubuntu2004"
        log.vm.network "private_network", ip: "172.16.16.12"
      end      
end
