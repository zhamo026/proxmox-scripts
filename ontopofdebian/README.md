# Install proxmox pve

1.By SSH login into the CLI and run these commands

```bash
apt update && upgrage  #uptodate

hostname --ip-address  #confirm your ip with any of the following commands
ip r
ip address show
                      #install it 

echo "deb [arch=amd64] http://download.proxmox.com/debian/pve bookworm pve-no-subscription" > /etc/apt/sources.list.d/pve-install-repo.list
```
update they keyerings

```bash
lvremove /dev/pve/data
lvresize -l +100%FREE /dev/pve/root
resize2fs /dev/mapper/pve-root
```
