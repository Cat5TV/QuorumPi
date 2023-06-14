# QuorumPi
Proxmox Quorum server for Raspberry Pi

This tool allows you to boot up a Raspberry Pi single board computer to provide quorum to a Proxmox cluster containing an even number of servers. Proxmox requires an odd number of servers for High Availability clusters (HA) so QuorumPi provides quorum without the need of an odd server (for example, you can now have HA with only 2 servers).

Documentation will come in time, but it's as simple as this:
- Flash the image and boot your ethernet-connected Raspberry Pi (DO NOT use WiFi),
- SSH to your Raspberry Pi. Login: `baldnerd` Password: `baldnerd`
- Type: `sudo activate` and follow the prompts,
- Create your cluster as normal in Proxmox,
- Copy the join information,
- Click `Join Cluster` and paste the join information. Enter the IP address of your QuorumPi server as well as the password you created while activating it,
- Now, run this command on all other servers on your cluster (as root): `apt update && apt -y install corosync-qdevice && pvecm qdevice setup <IP of QuorumPi> -f`

You don't need to build it yourself. Instead, download the ready-to-deploy image from https://drive.google.com/file/d/1EFLabdQOiJ4gtEZNoe3EgxWI5o9RNgr-/view?usp=sharing
