Standar Installation
Thanks to this sources
[helper-scripts](https://helper-scripts.com/)

remove repositories
```bash
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/post-pve-install.sh)"
```
remove LVM if auto added

```bash
lvremove /dev/pve/data
```
```bash
lvresize -l +100%FREE /dev/pve/root
```
```bash
resize2fs /dev/mapper/pve-root
```
