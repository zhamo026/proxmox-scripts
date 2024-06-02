Standar Installation
Thanks to these sources
[helper-scripts](https://helper-scripts.com/)
[forum.proxmox.com/](https://forum.proxmox.com/threads/can-i-remove-local-and-local-lvm.122850/)

remove repositories
```bash
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/post-pve-install.sh)"
```
remove LVM if auto added
remove it from the proxmox server direcly 
```bash
lvremove /dev/pve/data -y
```
```bash
lvresize -l +100%FREE /dev/pve/root
```
```bash
resize2fs /dev/mapper/pve-root
```
