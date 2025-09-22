## 2025-09-22 17:51:18
```bash
$ sudo apt install -y dnsmasq
````

```
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Reading package lists...
Building dependency tree...
Reading state information...
The following package was automatically installed and is no longer required:
  libllvm19
Use 'sudo apt autoremove' to remove it.
The following NEW packages will be installed:
  dnsmasq
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.9 kB of archives.
After this operation, 88.1 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 dnsmasq all 2.90-2ubuntu0.1 [17.9 kB]
Fetched 17.9 kB in 0s (56.5 kB/s)
Selecting previously unselected package dnsmasq.
(Reading database ... 
(Reading database ... 5%
...
(Reading database ... 100%
(Reading database ... 159365 files and directories currently installed.)
Preparing to unpack .../dnsmasq_2.90-2ubuntu0.1_all.deb ...
Unpacking dnsmasq (2.90-2ubuntu0.1) ...
Setting up dnsmasq (2.90-2ubuntu0.1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/dnsmasq.service → /usr/lib/systemd/system/dnsmasq.service.

Could not execute systemctl:  at /usr/bin/deb-systemd-invoke line 148.
```

## 2025-09-22 17:54:10

```bash
$ sudo nano /etc/dnsmasq.conf
```

```
listen-address=127.0.0.1
address=/app.lab.test/192.168.1.200
address=/db.lab.test/192.168.1.201
```

## 2025-09-22 17:56:13

```bash
$ systemctl restart dnsmasq
```

```
Job for dnsmasq.service failed because the control process exited with error code.
See "systemctl status dnsmasq.service" and "journalctl -xeu dnsmasq.service" for details.
```

## 2025-09-22 17:57:32

```bash
$ sudo systemctl status dnsmasq -n 30
```

```
× dnsmasq.service - dnsmasq - A lightweight DHCP and caching DNS server
     Loaded: loaded (/usr/lib/systemd/system/dnsmasq.service; enabled; preset: enabled)
     Active: failed (Result: exit-code) since Mon 2025-09-22 17:56:14 EEST; 1min 17s ago
...
Sep 22 17:56:14 user1-VirtualBox dnsmasq[5783]: FAILED to start up
Sep 22 17:56:14 user1-VirtualBox systemd[1]: dnsmasq.service: Failed with result 'exit-code'.
```

## 2025-09-22 18:02:05

```bash
$ ss -tulpn
```

```
Netid State  Recv-Q Send-Q Local Address:Port  Peer Address:PortProcess
udp   UNCONN 0      0            0.0.0.0:5353       0.0.0.0:*          
udp   UNCONN 0      0         127.0.0.54:53         0.0.0.0:*          
udp   UNCONN 0      0      127.0.0.53%lo:53         0.0.0.0:*          
...
```

## 2025-09-22 18:05:59

```bash
$ sudo cp /etc/dnsmasq.conf /etc/dnsmasq.conf.bak
```

## 2025-09-22 18:10:23

```bash
$ systemctl restart dnsmasq
```

```
Job for dnsmasq.service failed because the control process exited with error code.
See "systemctl status dnsmasq.service" and "journalctl -xeu dnsmasq.service" for details.
```

## 2025-09-22 18:11:31

```bash
$ sudo nano /etc/dnsmasq.conf
```

```
no-resolv
listen-address=192.168.1.150
bind-interfaces
server=1.1.1.1
server=8.8.8.8

address=/app.lab.test/192.168.1.200
address=/db.lab.test/192.168.1.201
```

## 2025-09-22 18:12:54

```bash
$ systemctl restart dnsmasq
```

## 2025-09-22 18:13:19

```bash
$ sudo systemctl status dnsmasq --no-pager -n 20
```

```
● dnsmasq.service - dnsmasq - A lightweight DHCP and caching DNS server
     Loaded: loaded (/usr/lib/systemd/system/dnsmasq.service; enabled; preset: enabled)
     Active: active (running) since Mon 2025-09-22 18:12:55 EEST; 23s ago
...
Sep 22 18:12:55 user1-VirtualBox systemd[1]: Started dnsmasq.service - dnsmasq - A lightweight DHCP and caching DNS server.
```

## 2025-09-22 18:14:42

```bash
$ dig @192.168.1.150 app.lab.test
```

```
;; ANSWER SECTION:
app.lab.test.		0	IN	A	192.168.1.200
```

## 2025-09-22 18:15:07

```bash
$ dig @192.168.1.150 db.lab.test
```

```
;; ANSWER SECTION:
db.lab.test.		0	IN	A	192.168.1.201
```

## 2025-09-22 18:15:55

```bash
$ sudo resolvect dns enp0s3 192.168.1.150
```

```
sudo: resolvect: command not found
```

## 2025-09-22 18:16:03

```bash
$ sudo resolvectl dns enp0s3 192.168.1.150
```

## 2025-09-22 18:16:58

```bash
$ ping -c2 app.lab.test
```

```
PING app.lab.test (192.168.1.200) 56(84) bytes of data.
From user1-VirtualBox (192.168.1.150) icmp_seq=1 Destination Host Unreachable
...
```

## 2025-09-22 18:17:16

```bash
$ ping -c2 db.lab.test
```

```
PING db.lab.test (192.168.1.201) 56(84) bytes of data.
From user1-VirtualBox (192.168.1.150) icmp_seq=1 Destination Host Unreachable
...
```

## 2025-09-22 18:18:42

```bash
$ dig app.lab.test
```

```
;; ANSWER SECTION:
app.lab.test.		0	IN	A	192.168.1.200
;; SERVER: 127.0.0.53#53(127.0.0.53)
```

```
