
Vagrant.configure('2') do |config|

    ## VirtualBox is the only provider I had access to that didn't crap out on networking so for now this is vbox-only
  ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

  config.vm.provider "virtualbox" do |v| 
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

  config.vm.box = 'centos/7'

  config.vm.define 'master' do |master|
    master.vm.hostname = 'master'
    master.vm.provision :shell, path: 'provision-master'
    master.vm.network "private_network", ip: '192.168.121.110'
  end

  config.vm.define 'node01' do |node|
    node.vm.provision :shell, path: 'provision-node'
    node.vm.hostname = 'node01'
    node.vm.network "private_network", ip: '192.168.121.111'
  end

  config.vm.define 'node02' do |node|
    node.vm.provision :shell, path: 'provision-node'
    node.vm.hostname = 'node02'
    node.vm.network "private_network", ip: '192.168.121.112'
  end

  config.vm.define 'node03' do |node|
    node.vm.provision :shell, path: 'provision-node'
    node.vm.hostname = 'node03'
    node.vm.network "private_network", ip: '192.168.121.113'
  end

end

# vim: ft=ruby
