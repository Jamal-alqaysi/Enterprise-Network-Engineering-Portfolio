

```
sudo nmcli connection modify "Wired connection 1" \
 ipv4.method manual \
 ipv4.addresses 192.168.99.10/24 \
 ipv4.gateway 192.168.99.254

sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```



