# Vagrant Hacks

## Reboot

This adds the reboot Capability to Linux VM's.

Move reboot_cap/plugin.rb to /opt/vagrant/embedded/gems/2.2.4/gems/vagrant-2.2.4/plugins/guests/linux/ and reboot_cap/reboot.rb to /opt/vagrant/embedded/gems/2.2.4/gems/vagrant-2.2.4/plugins/guests/linux/cap/.

After that you can add the reboot option to the shell Provisioner:

```
master.vm.provision "shell", inline: "do something", :reboot => true
```
