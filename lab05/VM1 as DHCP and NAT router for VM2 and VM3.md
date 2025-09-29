## 2025-09-25 18:25:34

```bash
$ ip -br a
```

```
lo               UNKNOWN        127.0.0.1/8 ::1/128 
enp0s3           UP             192.168.1.150/24 fe80::a00:27ff:feb1:1e94/64 
enp0s8           UP             192.168.56.10/24 fe80::a00:27ff:fe8e:b80c/64 
```

## 2025-09-25 18:26:10

```bash
$ sudo sysctl -w net.ipv4.ip_forward=1
```

```
net.ipv4.ip_forward = 1
```

## 2025-09-25 18:27:31

```bash
$ echo net.ipv4.ip_forward=1
```

```
net.ipv4.ip_forward=1
```

## 2025-09-25 18:30:49

```bash
$ sudo sysctl -p
```

```
net.ipv4.ip_forward = 1
```

## 2025-09-25 18:42:05

```bash
$ sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
```

```
```

## 2025-09-25 18:58:19

```bash
$ sudo iptables -L FORWARD -n -v
```

```
Chain FORWARD (policy DROP 4284 packets, 283K bytes)
 pkts bytes target     prot opt in     out     source               destination         
 4401  292K ufw-before-logging-forward  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
 4401  292K ufw-before-forward  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
 4284  283K ufw-after-forward  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
 4284  283K ufw-after-logging-forward  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
 4284  283K ufw-reject-forward  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
 4284  283K ufw-track-forward  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
```

## 2025-09-25 19:02:25

```bash
$ sudo iptables -t nat -C POSTROUTING -o enp0s3 -j MASQUERADE
```

```
```

## 2025-09-25 19:03:01

```bash
$ sudo iptables -C FORWARD -i enp0s8 -o enp0s3 -j ACCEPT
```

```
```

## 2025-09-25 19:03:20

```bash
$ sudo iptables -C FORWARD -i enp0s3 -o enp0s8 -m state --state RELATED,ESTABLISHED -j ACCEPT
```

```
iptables: Bad rule (does a matching rule exist in that chain?).
```

## VM2

```bash
user1@user2-VirtualBox2:~$ ping 8.8.8.8
```

```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=114 time=11.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=114 time=11.2 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=114 time=11.1 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=114 time=14.3 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=114 time=11.1 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=114 time=11.6 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=114 time=10.9 ms
64 bytes from 8.8.8.8: icmp_seq=8 ttl=114 time=13.8 ms
```

## VM2

```bash
user1@user2-VirtualBox2:~$ ping google.com
```

```
PING google.com (216.58.210.142) 56(84) bytes of data.
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=1 ttl=114 time=12.6 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=2 ttl=114 time=14.6 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=3 ttl=114 time=14.5 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=4 ttl=114 time=14.7 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=5 ttl=114 time=14.7 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=6 ttl=114 time=14.7 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=7 ttl=114 time=14.5 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=8 ttl=114 time=14.7 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=9 ttl=114 time=15.2 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=10 ttl=114 time=15.1 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=11 ttl=114 time=15.1 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=12 ttl=114 time=15.2 ms
```

## VM3

```bash
vm3user1@vm3user1-VirtualBox:~$ ping 8.8.8.8
```

```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=114 time=11.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=114 time=9.29 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=114 time=11.1 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=114 time=11.4 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=114 time=14.3 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=114 time=11.0 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=114 time=11.5 ms
64 bytes from 8.8.8.8: icmp_seq=8 ttl=114 time=11.2 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=114 time=12.6 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=114 time=11.1 ms
64 bytes from 8.8.8.8: icmp_seq=11 ttl=114 time=12.6 ms
64 bytes from 8.8.8.8: icmp_seq=12 ttl=114 time=11.0 ms
^C
--- 8.8.8.8 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 111413ms
rtt min/avg/max/mdev = 9.286/11.437/14.323/1.195 ms
```

## VM3

```bash
vm3user1@vm3user1-VirtualBox:~$ ping google.com
```

```
PING google.com (216.58.210.142) 56(84) bytes of data.
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=1 ttl=114 time=12.7 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=2 ttl=114 time=14.3 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=3 ttl=114 time=15.4 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=4 ttl=114 time=16.3 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=5 ttl=114 time=14.7 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=6 ttl=114 time=15.2 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=7 ttl=114 time=14.7 ms
64 bytes from mad06s09-in-f14.1e100.net (216.58.210.142): icmp_seq=8 ttl=114 time=15.3 ms
^C
--- google.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7643ms
```

