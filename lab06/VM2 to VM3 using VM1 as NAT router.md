## VM1 ROUTER

```bash
user1@user1-VirtualBox:~$ ip -br a
```

```
lo        UNKNOWN    127.0.0.1/8 ::1/128
enp0s3    UP         192.168.1.150/24 fe80::a00:27ff:feb1:e904/64
enp0s8    UP         192.168.56.10/24 fe80::a00:27ff:fe8e:b80c/64
```

## VM1 ROUTER

```bash
user1@user1-VirtualBox:~$ cat /proc/sys/net/ipv4/ip_forward
```

```
1
```

## VM1 ROUTER

```bash
user1@user1-VirtualBox:~$ sudo ss -ulpn | grep dhcp
```

```
[sudo] password for user1: 
UNCONN  0  0  0.0.0.0:67  0.0.0.0:*  users:(("dhcpd",pid=1590,fd=7))
```

## VM1 ROUTER

```bash
user1@user1-VirtualBox:~$ journalctl -u isc-dhcp-server --no-pager | tail -n 10
```

```
Sep 26 13:32:15 user1-VirtualBox dhcpd[1590]: DHCPACK on 192.168.56.50 to 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 26 13:32:11 user1-VirtualBox dhcpd[1590]: DHCPREQUEST for 192.168.56.50 from 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 26 13:37:11 user1-VirtualBox dhcpd[1590]: DHCPACK on 192.168.56.50 to 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 26 13:37:11 user1-VirtualBox dhcpd[1590]: DHCPREQUEST for 192.168.56.50 from 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 26 13:42:15 user1-VirtualBox dhcpd[1590]: DHCPACK on 192.168.56.50 to 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 26 13:47:15 user1-VirtualBox dhcpd[1590]: DHCPREQUEST for 192.168.56.50 from 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 26 13:47:15 user1-VirtualBox dhcpd[1590]: Wrote 2 leases to leases file.
Sep 26 13:47:15 user1-VirtualBox dhcpd[1590]: DHCPACK on 192.168.56.50 to 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
```

## VM1 ROUTER

```bash
user1@user1-VirtualBox:~$ sudo tcpdump -i enp0s8 -n
```

```
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on enp0s8, link-type EN10MB (Ethernet), snapshot length 262144 bytes
13:50:19.476383 IP 192.168.56.50.54635 > 1.1.1.1.53: 39615+ A? content-signature-2.cdn.mozilla.net. (53)
13:50:19.476383 IP 192.168.56.50.54635 > 1.1.1.1.53: 39615+ AAAA? content-signature-2.cdn.mozilla.net. (53)
13:50:19.543621 IP 1.1.1.1.53 > 192.168.56.50.54635: 39615 2/0/0 CNAME content-signature-chains.prod.autograph.services.mozilla.net., AAAA 2600:1901:0:92a9:: (151)
13:50:19.543653 IP 1.1.1.1.53 > 192.168.56.50.54635: 39615 2/0/0 CNAME content-signature-chains.prod.autograph.services.mozilla.net., A 34.160.144.191 (139)
13:50:19.544119 IP 192.168.56.50.40508 > 34.160.144.191.443: Flags [S], seq 451320986, win 64240, options [mss 1460,sackOK,TS val 2017342708 ecr 0,nop,wscale 7], length 0
13:50:19.544320 IP 192.168.56.50.40590 > 34.160.144.191.443: Flags [S], seq 3519208594, win 64240, options [mss 1460,sackOK,TS val 2017342729 ecr 0,nop,wscale 7], length 0
13:50:19.559563 IP 34.160.144.191.443 > 192.168.56.50.40588: Flags [S.], seq 1355425274, ack 451320987, win 65535, options [mss 1412,sackOK,TS val 2872496769 ecr 2017342728,nop,wscale 8], length 0
....
```

## VM1 ROUTER

```bash
user1@user1-VirtualBox:~$ sudo iptables -t nat -L POSTROUTING -n -v
```

```
Chain POSTROUTING (policy ACCEPT 111 packets, 17298 bytes)
 pkts bytes target     prot opt in  out    source          destination
  212 20299 MASQUERADE  0    --  *   enp0s3 192.168.56.0/24 0.0.0.0/0
```

## VM2 CLIENT

```bash
user1@user2-VirtualBox2:~$ ip -br a
```

```
lo        UNKNOWN    127.0.0.1/8 ::1/128
enp0s3    UP         192.168.56.50/24 fe80::a00:27ff:fea5:b887/64
```

## VM2 CLIENT

```bash
user1@user2-VirtualBox2:~$ ip -br a
```

```
lo        UNKNOWN    127.0.0.1/8 ::1/128
enp0s3    UP         192.168.56.50/24 fe80::a00:27ff:fea5:b887/64
```

## VM2 CLIENT

```bash
user1@user2-VirtualBox2:~$ ping 8.8.8.8
```

```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=114 time=11.3 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=114 time=11.2 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=114 time=8.92 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=114 time=11.0 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=114 time=11.0 ms
^C
--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4236ms
rtt min/avg/max/mdev = 8.924/10.704/11.336/0.897 ms
```

## VM2 CLIENT

```bash
user1@user2-VirtualBox2:~$ ping google.com
```

```
PING google.com (216.58.210.142) 56(84) bytes of data.
64 bytes from 216.58.210.142: icmp_seq=1 ttl=114 time=12.8 ms
64 bytes from 216.58.210.142: icmp_seq=2 ttl=114 time=12.5 ms
^C
--- google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1147ms
rtt min/avg/max/mdev = 12.540/12.682/12.824/0.142 ms
```

## VM3 SERVER

```bash
vm3user1@vm3user1-VirtualBox:/$ ip -br a
```

```
lo        UNKNOWN    127.0.0.1/8 ::1/128
enp0s3    UP         192.168.1.200/24 fe80::a00:27ff:fe35:cef2/64 fe80::8a7f:1157:3492:45da/64
```

## VM3 SERVER

```bash
vm3user1@vm3user1-VirtualBox:/$ sudo apt install -y nginx
```

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following package was automatically installed and is no longer required:
  libllvm19
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  nginx-common
Suggested packages:
  fcgiwrap nginx-doc
The following NEW packages will be installed:
  nginx nginx-common
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 564 kB of archives.
After this operation, 1,596 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 nginx-common all 1.24.0-2ubuntu7.5 [43.4 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 nginx amd64 1.24.0-2ubuntu7.5 [520 kB]
Fetched 564 kB in 0s (1,612 kB/s)
Preconfiguring packages ...
Selecting previously unselected package nginx-common.
(Reading database ... 189385 files and directories currently installed.)
Preparing to unpack .../nginx-common_1.24.0-2ubuntu7.5_all.deb ...
Unpacking nginx-common (1.24.0-2ubuntu7.5) ...
Selecting previously unselected package nginx.
Preparing to unpack .../nginx_1.24.0-2ubuntu7.5_amd64.deb ...
Unpacking nginx (1.24.0-2ubuntu7.5) ...
Setting up nginx-common (1.24.0-2ubuntu7.5) ...
Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /usr/lib/systemd/system/nginx.service.
Setting up nginx (1.24.0-2ubuntu7.5) ...
  * Upgrading binary nginx
    [ OK ]
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for ufw (0.36.2-6) ...
```

## VM3 SERVER

```bash
vm3user1@vm3user1-VirtualBox:/$ sudo systemctl enable --now nginx
```

```
Synchronizing state of nginx.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install enable nginx
```

## VM2 CLIENT

```bash
user1@user2-VirtualBox2:~$ curl http://192.168.1.200
```

```html
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

## VM2 CLIENT

```bash
user1@user2-VirtualBox2:~$ traceroute 192.168.1.200
```

```
traceroute to 192.168.1.200 (192.168.1.200), 64 hops max
 1  192.168.56.10  0.266ms  0.149ms  0.138ms
 2  192.168.1.200  0.640ms  0.306ms  0.324ms
```

## VM1 ROUTER

```bash
user1@user1-VirtualBox:~$ sudo tcpdump -i enp0s3 -nn host 192.168.1.200
```

```
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on enp0s3, link-type EN10MB (Ethernet), snapshot length 262144 bytes
14:20:41.743955 IP 192.168.1.150.60478 > 192.168.1.200.80: Flags [S], seq 2418003865, win 64240, options [mss 1460,sackOK,TS val 3252022272 ecr 0,nop,wscale 7], length 0
14:20:41.744169 IP 192.168.1.200.80 > 192.168.1.150.60478: Flags [S.], seq 3450476179, ack 2418003866, win 65160, options [mss 1460,sackOK,TS val 1066406821 ecr 3252022272,nop,wscale 7], length 0
14:20:41.744321 IP 192.168.1.150.60478 > 192.168.1.200.80: Flags [.], ack 1, win 502, options [nop,nop,TS val 3252022273 ecr 1066406821], length 0
14:20:41.744382 IP 192.168.1.150.60478 > 192.168.1.200.80: Flags [P.], seq 1:77, ack 1, win 502, options [nop,nop,TS val 3252022273 ecr 1066406821], length 76: HTTP: GET / HTTP/1.1
14:20:41.744847 IP 192.168.1.200.80 > 192.168.1.150.60478: Flags [.], ack 77, win 509, options [nop,nop,TS val 1066406822 ecr 3252022273], length 0
14:20:41.744993 IP 192.168.1.200.80 > 192.168.1.150.60478: Flags [P.], seq 1:863, ack 77, win 509, options [nop,nop,TS val 1066406822 ecr 3252022273], length 862: HTTP: HTTP/1.1 200 OK
14:20:41.745112 IP 192.168.1.150.60478 > 192.168.1.200.80: Flags [.], ack 863, win 496, options [nop,nop,TS val 3252022273 ecr 1066406822], length 0
14:20:41.745284 IP 192.168.1.150.60478 > 192.168.1.200.80: Flags [F.], seq 77, ack 863, win 496, options [nop,nop,TS val 3252022274 ecr 1066406822], length 0
14:20:41.745432 IP 192.168.1.200.80 > 192.168.1.150.60478: Flags [F.], seq 863, ack 78, win 509, options [nop,nop,TS val 1066406823 ecr 3252022274], length 0
14:20:41.745569 IP 192.168.1.150.60478 > 192.168.1.200.80: Flags [.], ack 864, win 496, options [nop,nop,TS val 3252022274 ecr 1066406823], length 0
14:20:47.036342 ARP, Request who-has 192.168.1.200 tell 192.168.1.150, length 28
14:20:47.036519 ARP, Reply 192.168.1.200 is-at 08:00:27:35:ce:f2, length 46
```

