# Install proxmox pve

1. SSH into the CLI and run these commands

```bash
#check ip and gateway
hostname --ip-address  
ip r
ip address show
```
if your ip isn't showing you need to add the ip to the local host file 
```bash
hostnamectl set-hostname [addhostname*]
exec bash

sudo nano /etc/hosts
192.168.x.x [retypehostname*]

confirm the ip  once more:
hostname
hostname --ip-address
```
add dependency repositories

```bash
sudo apt install curl software-properties-common apt-transport-https ca-certificates gnupg2
```

                      #install it 
```bash
echo "deb [arch=amd64] http://download.proxmox.com/debian/pve bookworm pve-no-subscription" > /etc/apt/sources.list.d/pve-install-repo.list

#add it
wget https://enterprise.proxmox.com/debian/proxmox-release-bookworm.gpg -O /etc/apt/trusted.gpg.d/proxmox-release-bookworm.gpg  
```
#apt update && apt full-upgrade

```

# Install the Proxmox Kernel
```bash
apt install proxmox-default-kernel -y


apt install proxmox-ve postfix open-iscsi chrony
```
Check proxmor port
```bash
ss -tunelp | grep 8006
```
Check kernel and remove kernel
```bash
#check
dpkg -l | grep linux-image
#remove
apt remove linux-image-amd64 'linux-image-6.1*' 
```

update grube
update-grub

remove prober
apt remove os-prober

reboot




update they keyerings

```bash
lvremove /dev/pve/data
lvresize -l +100%FREE /dev/pve/root
resize2fs /dev/mapper/pve-root
```
