## On systems with a dnsmasq/systemd-resolved unit consuming port 53

```
cp /etc/systemd/resolved.conf /etc/systemd/resolved.conf.bak
```
```
cat <<EOF | tee /etc/systemd/resolved.conf
[Resolve]
DNS=8.8.8.8
DNSStubListener=no
EOF
```
```
mkdir /run/systemd/resolve
ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf
```
```
systemctl restart systemd-resolved.service
```
```
cat /etc/resolve.conf
```
```
reboot
```
### Now you are ready to deploy cloudctl