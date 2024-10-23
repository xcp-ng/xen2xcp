# xen2xcp

This script is here to help migrating VMs from a vanilla Xen setup, where you are running Xen on a Linux distribution, using `xl` to manage your VMs, and also plain text configuration files.

1. Ensure you have backups before attempting the migration.
1. Get that script in your current `dom0`.
1. For each VM:
  1. Shut it down.
  1. Run the script, VM by VM with for example: `./xen2xcp.py -c /etc/xen/vm1.cfg -n vm1 -s xcp_host_1 --username=root --password="mypassword" --no-ssl`. You can use a hostname or the IP address of your XCP-ng host (name `xcp_host_1` here)
  1. Your disks are streamed while the configuration file is "translated" to a VM object in your XCP-ng host.
  1. As soon it's done, you should be able to boot your VM on destination.

If you have an error telling you that you don't have a default SR, please choose a default SR on your XCP-ng pool (in XO, Home/Storage, hover on the storage you want to put by default, there's an icon for it).

*Note: This script is provided as is, and may have rough edges. If you have issues, please report them.*
