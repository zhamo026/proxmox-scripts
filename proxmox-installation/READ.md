# Standar installation


add the intel support
```bash
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/microcode.sh)"
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
add user
```bash
adduser #name
#add password
```


install a desktop enviroment if in a laptop
```bash
apt install kde-plasma-desktop -y
```

or add an nas interface
```bash
####
```
remove repositories
```bash
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/post-pve-install.sh)"
```


Thanks to these sources
[helper-scripts](https://helper-scripts.com/)
[forum.proxmox.com/](https://forum.proxmox.com/threads/can-i-remove-local-and-local-lvm.122850/)
