# Installation
[prxomoxwiki for more info](https://pve.proxmox.com/wiki/Install_Proxmox_VE_on_Debian_12_Bookworm)

Check the ip 
```bash
#check ip and gateway
hostname --ip-address  
ip r
ip address show
```
SSH into the CLI and set an static IP and hostname must match your hostname

enable SSH
```bash
nano /etc/ssh/sshd_config
#uncomment port 22 [add your port]
#if necessary uncomment
#PermitRootLogin and add yes
```
Modify or set a static ip
```bash
nano /etc/network/interfaces
#example
#auto enpxx
#iface enpxx inet static
        #address 192.168.x.x/24
        #netmask 255.255.xxx.x
        #gateway 192.168.x.x
```
to set a hostname
```bash
hostnamectl set-hostname [addhostname*]
```
```bash
exec bash
```

to set the host ipaddress
```bash
nano /etc/hosts
#example
#201.0.0.0   local.domain local add local domain
#192.168.x.x [checkyourhostname*]
```
confirm the ip  once more:
```bash
hostname
hostname --ip-address
```
reboot the system
```bash
reboot

#or reload network if running directly on CLI
#ifdown enpxx
#ifup enpxx
```

Add repositories
```bash
echo "deb [arch=amd64] http://download.proxmox.com/debian/pve bookworm pve-no-subscription" > /etc/apt/sources.list.d/pve-install-repo.list -y
```
```bash
wget https://enterprise.proxmox.com/debian/proxmox-release-bookworm.gpg -O /etc/apt/trusted.gpg.d/proxmox-release-bookworm.gpg
```
Update
```bash
apt update && apt full-upgrade -y
```
Install it
```bash
apt install proxmox-ve postfix open-iscsi chrony -y
```

Check proxmox listening port
```bash
ss -tunelp | grep 8006
```

Remove prober
```bash
apt remove os-prober
```
reboot
```bash
reboot
```

