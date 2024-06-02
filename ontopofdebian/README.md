# Installation

1. Check the ip 

```bash
#check ip and gateway
hostname --ip-address  
ip r
ip address show
```

2. SSH into the CLI and set an static IP and hostname must match your hostname

```bash

#to SSH
nano /etc/ssh/sshd_config
#uncomment port 22 [add your port]
#if necessary uncomment
#PermitRootLogin and add yes



#modify or set  a sstatic ip
nano /etc/network/interfaces
#example
#auto enpxx
#iface enpxx inet static
        #address 192.168.x.x/24
        #netmask 255.255.xxx.x
        #gateway 192.168.x.x

# to set a hostname
hostnamectl set-hostname [addhostname*]
exec bash

#to set the host ipaddress
nano /etc/hosts
#192.168.x.x [retypehostname*]

#confirm the ip  once more:
hostname
hostname --ip-address


reboot
#or reload network if running directly on CLI
#ifdown enpxx
#ifup enpxx
```


4. Add dependency repositories
```bash
apt install curl software-properties-common apt-transport-https ca-certificates gnupg2
```
5. Install it 
```bash
echo "deb [arch=amd64] http://download.proxmox.com/debian/pve bookworm pve-no-subscription" > /etc/apt/sources.list.d/pve-install-repo.list -y
```
6. Add it
```bash
wget https://enterprise.proxmox.com/debian/proxmox-release-bookworm.gpg -O /etc/apt/trusted.gpg.d/proxmox-release-bookworm.gpg
```
7. Update
```bash
apt update && apt full-upgrade -y
```
8. Install the Proxmox Kernel
```bash
apt install proxmox-default-kernel -y
```
```bash
systemctl reboot
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
