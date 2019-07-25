# Vagrant Hacks

## Reboot

This adds the reboot Capability to Linux VM's.

Move reboot_cap/plugin.rb to /opt/vagrant/embedded/gems/2.2.4/gems/vagrant-2.2.4/plugins/guests/linux/ and reboot_cap/reboot.rb to /opt/vagrant/embedded/gems/2.2.4/gems/vagrant-2.2.4/plugins/guests/linux/cap/.

After that you can add the reboot option to the shell Provisioner:

```
master.vm.provision "shell", inline: "do something", :reboot => true
```

## DNS Server

This is specific for the libvirt provider with the [vagrant-libvirt](https://github.com/vagrant-libvirt/vagrant-libvirt) plugin and netplan capable guests like Ubuntu18.04.

Move dns_server/create_network_interfaces.rb to /home/mwyrsch/.vagrant.d/gems/2.4.4/gems/vagrant-libvirt-0.0.45/lib/vagrant-libvirt/action/create_network_interfaces.rb and dns_server/configure_networks.rb to /opt/vagrant/embedded/gems/2.2.3/gems/vagrant-2.2.3/plugins/guests/debian/cap/configure_networks.rb.

After that you can define dns server (and search domains) for the interfaces.

```
master.vm.network :private_network, :ip => "#{SUBNET}.5", :gateway => "#{SUBNET}.1", :dns_servers => "#{SUBNET}.1", :dns_search => "foo"
```
