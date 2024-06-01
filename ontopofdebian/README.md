# Installation

1. Check the ip 

```bash
#check ip and gateway
hostname --ip-address  
ip r
ip address show
```

2. SSH into the CLI and run these commands
```bash
nano /etc/ssh/sshd_config
uncomment port 22 [add your port]
if necessary uncomment
PermitRootLogin and add yes

reboot
```
3. If your ip isn't showing you need to add the ip to the local host file 
```bash
hostnamectl set-hostname [addhostname*]
exec bash

sudo nano /etc/hosts
192.168.x.x [retypehostname*]

confirm the ip  once more:
hostname
hostname --ip-address
```

4. Add dependency repositories
```bash
sudo apt install curl software-properties-common apt-transport-https ca-certificates gnupg2
```
5. Install it 
```bash
echo "deb [arch=amd64] http://download.proxmox.com/debian/pve bookworm pve-no-subscription" > /etc/apt/sources.list.d/pve-install-repo.list
```
6. Add it
```bash
wget https://enterprise.proxmox.com/debian/proxmox-release-bookworm.gpg -O /etc/apt/trusted.gpg.d/proxmox-release-bookworm.gpg  
```
7. Update
```bash
apt update && apt full-upgrade
```
8. Install the Proxmox Kernel
```bash
apt install proxmox-default-kernel -y
```
```bash
apt install proxmox-ve postfix open-iscsi chrony
```
9.Check proxmor port
```bash
ss -tunelp | grep 8006
```
10. Check kernel and remove kernel
```bash
#check
uname -r

dpkg -l | grep linux-image
#remove
apt remove linux-image-amd64 'linux-image-6.1*' 
```
11. Update the grubloader
```bash
update grub
```
12. Remove prober
```bash
apt remove os-prober
```
reboot
```bash
reboot
```


```bash
lvremove /dev/pve/data
lvresize -l +100%FREE /dev/pve/root
resize2fs /dev/mapper/pve-root
```
