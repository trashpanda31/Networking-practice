## 2025-09-22 17:42:25
```bash
$ ssh eliass@192.168.1.150
````

```
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.14.0-29-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

11 additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm

Last login: Mon Sep 22 17:41:11 2025 from 192.168.1.111
```

## 2025-09-22 17:43:02

```bash
$ logcmd ip -br a
```

```
lo               UNKNOWN        127.0.0.1/8 ::1/128 
enp0s3           UP             192.168.1.150/24 fe80::a00:27ff:feb1:1e94/64 
```

## 2025-09-22 17:43:20

```bash
$ resolvectl status
```

```
Global
         Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
  resolv.conf mode: stub

Link 2 (enp0s3)
    Current Scopes: DNS
         Protocols: +DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 1.1.1.1
       DNS Servers: 1.1.1.1 8.8.8.8
```

## 2025-09-22 17:43:43

```bash
$ logcmd ping 1.1.1.1
```

```
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=58 time=4.22 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=58 time=4.05 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=58 time=4.15 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=58 time=4.11 ms
64 bytes from 1.1.1.1: icmp_seq=5 ttl=58 time=1.84 ms
64 bytes from 1.1.1.1: icmp_seq=6 ttl=58 time=4.44 ms
64 bytes from 1.1.1.1: icmp_seq=7 ttl=58 time=4.27 ms
^C
```

## 2025-09-22 17:44:35

```bash
$ logcmd ping -c5 google.com
```

```
PING google.com (216.58.210.142) 56(84) bytes of data.
64 bytes from mad06s09-in-f142.1e100.net (216.58.210.142): icmp_seq=1 ttl=115 time=14.8 ms
64 bytes from mad06s09-in-f142.1e100.net (216.58.210.142): icmp_seq=2 ttl=115 time=14.4 ms
64 bytes from mad06s09-in-f142.1e100.net (216.58.210.142): icmp_seq=3 ttl=115 time=14.5 ms
64 bytes from mad06s09-in-f142.1e100.net (216.58.210.142): icmp_seq=4 ttl=115 time=14.3 ms
64 bytes from mad06s09-in-f142.1e100.net (216.58.210.142): icmp_seq=5 ttl=115 time=14.7 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4031ms
rtt min/avg/max/mdev = 14.322/14.520/14.752/0.167 ms
```

## 2025-09-22 17:44:54

```bash
$ logcmd host google.com
```

```
google.com has address 216.58.210.142
google.com has IPv6 address 2a00:1450:4026:804::200e
google.com mail is handled by 10 smtp.google.com.
```

## 2025-09-22 17:45:17

```bash
$ logcmd dig google.com
```

```
; <<>> DiG 9.18.39-0ubuntu0.24.04.1-Ubuntu <<>> google.com
;; global options: +cmd
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24059
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		22	IN	A	216.58.210.142

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Mon Sep 22 17:45:17 EEST 2025
;; MSG SIZE  rcvd: 55
```

## 2025-09-22 17:45:46

```bash
$ logcmd nslookup google.com
```

```
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
Name:	google.com
Address: 216.58.210.142
Name:	google.com
Address: 2a00:1450:4026:804::200e
```

## 2025-09-22 17:47:44

```bash
$ sudo bash -c 'printf "\n10.10.10.10 fake.lab.test\n" >> /etc/hosts'
```

```
[sudo] password for eliass: 
Sorry, try again.
[sudo] password for eliass: 
```

## 2025-09-22 17:48:25

```bash
$ logcmd ping -c5 fake.lab.test
```

```
PING fake.lab.test (10.10.10.10) 56(84) bytes of data.

--- fake.lab.test ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4122ms
```

## 2025-09-22 17:49:00

```bash
$ logout
```

```
Connection to 192.168.1.150 closed.
```
