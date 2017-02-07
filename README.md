I was dealing with the same problem for months and today I decided I would find a better fix. Here is what I did on the machine I was using as a Template.

For good administration practices back up both files before editing.

You have two offending/target files:

```
/etc/sysconfig/network-scripts/ifcfg-eth0
/etc/udev/rules.d/70-persistent-net.rules
```
This will work for a static or dhcp address:

Open `/etc/sysconfig/network-scripts/ifcfg-eth0`

Delete the MAC Address line:  HWADDR=XX:11:22:XX:33:XX
Save the file.

Delete the file `/etc/udev/rules.d/70-persistent-net.rules` "it will be recreated after you restart the VM"

`sudo rm -f /etc/udev/rules.d/70-persistent-net.rules`

You can now clone your box and every clone will correctly deploy and display eth0.

If you do not use a template, you may complete these procedures on the actual VM just remember to re-initialize the NIC your in the VM software before you restart the machine.

*Source*

*http://askubuntu.com/questions/82322/how-do-i-fix-broken-networking-in-cloned-virtual-machines*