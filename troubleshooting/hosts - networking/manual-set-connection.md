1. Create Bridge
```
ip link add name vmbr0 type bridge
```

2. Turn on Physical Port
````
ip link set eno1 up
````

3. Set eno1 to use vmbr0
```
ip link set eno1 master vmbr0
```

4. Assign IP Address to Bridge
```
ip addr add 192.168.1.50/24 dev vmbr0
```

5. Turn Bridge on
```
ip link set vmbr0 up
```

6. Add Gateway
```
ip route add default via 192.68.1.1
```

7. Verify
```
ping google.com
```

