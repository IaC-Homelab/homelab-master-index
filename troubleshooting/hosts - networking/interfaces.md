/etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eno1
iface eno1 inet manual

auto vmbr0
iface vmbr0 inet static
        address 192.168.1.31
        netmask 255.255.255.0
        gateway 192.168.1.1
        bridge-ports eno1
        bridge-stp off
        bridge-fd 0

source /etc/network/interfaces.d/*
```