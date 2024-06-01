Standar Installation


#Troubleshooting 
change IP trhough the CLI if needed


nano /etc/network/interfaces

```bash
iface enp5s0 inet manual

auto vmbr0
iface vmbr0 inet dhcp       #edit it
    bridge-ports enp5s0
    bridge-stp off
bridge-fd 0
```
