
## 2025-09-17 15:17:26
```bash
$ echo hello world lab02
```
```
hello world lab02
```

## 2025-09-17 15:18:19
```bash
$ python3 -m http.server 9090
```
```

## 2025-09-17 15:18:55
```bash
$ ss -tulpn
```
```
Netid State  Recv-Q Send-Q Local Address:Port  Peer Address:PortProcess                             
udp   UNCONN 0      0            0.0.0.0:46473      0.0.0.0:*                                       
udp   UNCONN 0      0         127.0.0.54:53         0.0.0.0:*                                       
udp   UNCONN 0      0      127.0.0.53%lo:53         0.0.0.0:*                                       
udp   UNCONN 0      0        224.0.0.251:5353       0.0.0.0:*    users:(("opera",pid=4768,fd=313))  
udp   UNCONN 0      0        224.0.0.251:5353       0.0.0.0:*    users:(("opera",pid=4995,fd=70))   
udp   UNCONN 0      0            0.0.0.0:5353       0.0.0.0:*                                       
udp   UNCONN 0      0               [::]:33961         [::]:*                                       
udp   UNCONN 0      0               [::]:5353          [::]:*                                       
tcp   LISTEN 0      5            0.0.0.0:8080       0.0.0.0:*    users:(("python3",pid=172637,fd=3))
tcp   LISTEN 0      4096      127.0.0.54:53         0.0.0.0:*                                       
tcp   LISTEN 0      4096       127.0.0.1:631        0.0.0.0:*                                       
tcp   LISTEN 0      5            0.0.0.0:9090       0.0.0.0:*    users:(("python3",pid=307817,fd=3))
tcp   LISTEN 0      4096   127.0.0.53%lo:53         0.0.0.0:*                                       
tcp   LISTEN 0      4096           [::1]:631           [::]:*                                       
```

## 2025-09-17 15:19:54
```bash
$ curl -I http://127.0.0.1:9090
```
```
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0127.0.0.1 - - [17/Sep/2025 15:19:54] "HEAD / HTTP/1.1" 200 -
  0    87    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
HTTP/1.0 200 OK
Server: SimpleHTTP/0.6 Python/3.12.3
Date: Wed, 17 Sep 2025 12:19:54 GMT
Content-type: text/html
Content-Length: 87
Last-Modified: Wed, 17 Sep 2025 12:17:26 GMT

```

## 2025-09-17 15:20:06
```bash
$ ip a
```
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: enp9s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 04:42:1a:28:bb:80 brd ff:ff:ff:ff:ff:ff
3: wlp6s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 18:93:41:60:52:f7 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.111/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp6s0
       valid_lft 4196sec preferred_lft 4196sec
    inet6 fe80::b607:8687:782c:7470/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

## 2025-09-17 15:25:16
```bash
$ ss -tulpn
```
```
Netid State  Recv-Q Send-Q Local Address:Port  Peer Address:PortProcess                             
udp   UNCONN 0      0            0.0.0.0:46473      0.0.0.0:*                                       
udp   UNCONN 0      0         127.0.0.54:53         0.0.0.0:*                                       
udp   UNCONN 0      0      127.0.0.53%lo:53         0.0.0.0:*                                       
udp   UNCONN 0      0        224.0.0.251:5353       0.0.0.0:*    users:(("opera",pid=4768,fd=313))  
udp   UNCONN 0      0        224.0.0.251:5353       0.0.0.0:*    users:(("opera",pid=4995,fd=70))   
udp   UNCONN 0      0            0.0.0.0:5353       0.0.0.0:*                                       
udp   UNCONN 0      0               [::]:33961         [::]:*                                       
udp   UNCONN 0      0               [::]:5353          [::]:*                                       
tcp   LISTEN 0      5            0.0.0.0:8080       0.0.0.0:*    users:(("python3",pid=172637,fd=3))
tcp   LISTEN 0      4096      127.0.0.54:53         0.0.0.0:*                                       
tcp   LISTEN 0      4096       127.0.0.1:631        0.0.0.0:*                                       
tcp   LISTEN 0      5            0.0.0.0:9090       0.0.0.0:*    users:(("python3",pid=307817,fd=3))
tcp   LISTEN 0      4096   127.0.0.53%lo:53         0.0.0.0:*                                       
tcp   LISTEN 0      4096           [::1]:631           [::]:*                                       
```
192.168.1.231 - - [17/Sep/2025 15:28:42] "GET / HTTP/1.1" 200 -
192.168.1.231 - - [17/Sep/2025 15:28:53] "GET / HTTP/1.1" 200 -
192.168.1.231 - - [17/Sep/2025 15:28:53] code 404, message File not found
192.168.1.231 - - [17/Sep/2025 15:28:53] "GET /favicon.ico HTTP/1.1" 404 -

## 2025-09-17 15:30:38
```bash
$ sudo ufw deny 9090/tcp
```
```
Rule updated
Rule updated (v6)
```

## 2025-09-17 15:31:11
```bash
$ sudo tail -f /var/log/ufw.log
```
```
2025-09-17T15:22:24.916138+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:56:6f:d3:25:ee:d2:08:00 SRC=192.168.1.224 DST=192.168.1.111 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=51419 DPT=9090 WINDOW=65535 RES=0x00 SYN URGP=0 
2025-09-17T15:22:55.943146+03:00 eliass-System-Product-Name kernel: message repeated 2 times: [ [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:56:6f:d3:25:ee:d2:08:00 SRC=192.168.1.224 DST=192.168.1.111 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=51419 DPT=9090 WINDOW=65535 RES=0x00 SYN URGP=0 ]
2025-09-17T15:23:13.760152+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=26656 DF PROTO=2 
2025-09-17T15:24:54.113144+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:56:6f:d3:25:ee:d2:08:00 SRC=192.168.1.224 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=8484 PROTO=2 
2025-09-17T15:25:18.791150+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=33094 DF PROTO=2 
2025-09-17T15:25:22.990146+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39113 PROTO=2 
2025-09-17T15:27:23.823152+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=56840 DF PROTO=2 
2025-09-17T15:27:24.949141+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39123 PROTO=2 
2025-09-17T15:29:28.856158+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=200 DF PROTO=2 
2025-09-17T15:29:31.414146+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39130 PROTO=2 
2025-09-17T15:31:22.521146+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:56:6f:d3:25:ee:d2:08:00 SRC=192.168.1.224 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=56263 PROTO=2 
2025-09-17T15:31:33.783143+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=9965 DF PROTO=2 
2025-09-17T15:31:35.421143+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39138 PROTO=2 
2025-09-17T15:32:59.697146+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:56:6f:d3:25:ee:d2:08:00 SRC=192.168.1.224 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=33078 PROTO=2 

## 2025-09-17 15:33:14
```bash
$ sudo tail -f /var/log/ufw.log
```
```
2025-09-17T15:25:18.791150+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=33094 DF PROTO=2 
2025-09-17T15:25:22.990146+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39113 PROTO=2 
2025-09-17T15:27:23.823152+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=56840 DF PROTO=2 
2025-09-17T15:27:24.949141+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39123 PROTO=2 
2025-09-17T15:29:28.856158+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=200 DF PROTO=2 
2025-09-17T15:29:31.414146+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39130 PROTO=2 
2025-09-17T15:31:22.521146+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:56:6f:d3:25:ee:d2:08:00 SRC=192.168.1.224 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=56263 PROTO=2 
2025-09-17T15:31:33.783143+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=9965 DF PROTO=2 
2025-09-17T15:31:35.421143+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39138 PROTO=2 
2025-09-17T15:32:59.697146+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:56:6f:d3:25:ee:d2:08:00 SRC=192.168.1.224 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=33078 PROTO=2 
2025-09-17T15:33:38.918154+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23289 DF PROTO=2 
2025-09-17T15:33:39.435155+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39139 PROTO=2 
2025-09-17T15:35:43.948161+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=52862 DF PROTO=2 
2025-09-17T15:35:46.920144+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39140 PROTO=2 

## 2025-09-17 15:37:17
```bash
$ sudo ufw logging high
```
```
Logging enabled
```

## 2025-09-17 15:37:23
```bash
$ sudo tail -f /var/log/ufw.log
```
```
2025-09-17T15:29:31.414146+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39130 PROTO=2 
2025-09-17T15:31:22.521146+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:56:6f:d3:25:ee:d2:08:00 SRC=192.168.1.224 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=56263 PROTO=2 
2025-09-17T15:31:33.783143+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=9965 DF PROTO=2 
2025-09-17T15:31:35.421143+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39138 PROTO=2 
2025-09-17T15:32:59.697146+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:56:6f:d3:25:ee:d2:08:00 SRC=192.168.1.224 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=33078 PROTO=2 
2025-09-17T15:33:38.918154+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23289 DF PROTO=2 
2025-09-17T15:33:39.435155+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39139 PROTO=2 
2025-09-17T15:35:43.948161+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:01:c0:25:2f:6f:0b:45:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=52862 DF PROTO=2 
2025-09-17T15:35:46.920144+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39140 PROTO=2 
2025-09-17T15:37:01.465144+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:56:6f:d3:25:ee:d2:08:00 SRC=192.168.1.224 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=20376 PROTO=2 
2025-09-17T15:37:26.759141+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35175 DF PROTO=TCP SPT=54430 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:37:26.759147+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35176 DF PROTO=TCP SPT=54431 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:37:27.066138+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35177 DF PROTO=TCP SPT=54432 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:37:27.783138+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35178 DF PROTO=TCP SPT=54430 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:37:27.783141+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35179 DF PROTO=TCP SPT=54431 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:37:28.090137+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35180 DF PROTO=TCP SPT=54432 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:37:29.520169+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=35.190.80.1 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36208 DF PROTO=TCP SPT=51294 DPT=443 WINDOW=496 RES=0x00 ACK URGP=0 
2025-09-17T15:37:29.536136+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:c0:25:2f:6f:0b:45:08:00 SRC=35.190.80.1 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=119 ID=57352 PROTO=TCP SPT=443 DPT=51294 WINDOW=1042 RES=0x00 ACK URGP=0 
2025-09-17T15:37:29.831145+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35181 DF PROTO=TCP SPT=54430 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:37:29.831149+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35182 DF PROTO=TCP SPT=54431 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:37:30.036138+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35183 DF PROTO=TCP SPT=54432 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:37:33.616157+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=172.64.155.209 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=49689 DF PROTO=TCP SPT=57538 DPT=443 WINDOW=276 RES=0x00 ACK URGP=0 
2025-09-17T15:37:35.156139+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=172.64.148.235 LEN=80 TOS=0x00 PREC=0x00 TTL=64 ID=15220 DF PROTO=TCP SPT=44034 DPT=443 WINDOW=480 RES=0x00 ACK PSH URGP=0 

## 2025-09-17 15:40:07
```bash
$ sudo ufw delete deny 9090/tcp
```
```
Rule deleted
Rule deleted (v6)
```

## 2025-09-17 15:40:42
```bash
$ sudo ufw insert 1 log deny proto tcp from any to any port 90
```
```
ERROR: Invalid syntax

Usage: ufw COMMAND

Commands:
 enable                          enables the firewall
 disable                         disables the firewall
 default ARG                     set default policy
 logging LEVEL                   set logging to LEVEL
 allow ARGS                      add allow rule
 deny ARGS                       add deny rule
 reject ARGS                     add reject rule
 limit ARGS                      add limit rule
 delete RULE|NUM                 delete RULE
 insert NUM RULE                 insert RULE at NUM
 prepend RULE                    prepend RULE
 route RULE                      add route RULE
 route delete RULE|NUM           delete route RULE
 route insert NUM RULE           insert route RULE at NUM
 reload                          reload firewall
 reset                           reset firewall
 status                          show firewall status
 status numbered                 show firewall status as numbered list of RULES
 status verbose                  show verbose firewall status
 show ARG                        show firewall report
 version                         display version information

Application profile commands:
 app list                        list application profiles
 app info PROFILE                show information on PROFILE
 app update PROFILE              update PROFILE
 app default ARG                 set default application policy

```

## 2025-09-17 15:41:50
```bash
$ sudo ufw insert 1 deny log proto tcp from any to any port 90
```
```
Skipping inserting existing rule
Skipping inserting existing rule (v6)
```

## 2025-09-17 15:42:16
```bash
$ sudo tail -f /var/log/ufw.log
```
```
2025-09-17T15:41:59.724147+03:00 eliass-System-Product-Name kernel: [UFW ALLOW] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=239.255.255.250 LEN=193 TOS=0x00 PREC=0x00 TTL=1 ID=22770 DF PROTO=UDP SPT=33794 DPT=1900 LEN=173 
2025-09-17T15:42:00.272144+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:c0:25:2f:6f:0b:45:08:00 SRC=172.64.155.209 DST=192.168.1.111 LEN=366 TOS=0x00 PREC=0x00 TTL=58 ID=15572 DF PROTO=TCP SPT=443 DPT=42322 WINDOW=12 RES=0x00 ACK PSH URGP=0 
2025-09-17T15:42:00.653147+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=172.64.148.235 LEN=142 TOS=0x00 PREC=0x00 TTL=64 ID=50117 DF PROTO=TCP SPT=37072 DPT=443 WINDOW=476 RES=0x00 ACK PSH URGP=0 
2025-09-17T15:42:00.657141+03:00 eliass-System-Product-Name kernel: [UFW ALLOW] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=192.168.1.1 LEN=77 TOS=0x00 PREC=0x00 TTL=64 ID=1146 PROTO=UDP SPT=38331 DPT=53 LEN=57 
2025-09-17T15:42:00.657146+03:00 eliass-System-Product-Name kernel: [UFW ALLOW] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=192.168.1.1 LEN=77 TOS=0x00 PREC=0x00 TTL=64 ID=51417 PROTO=UDP SPT=51864 DPT=53 LEN=57 
2025-09-17T15:42:00.659141+03:00 eliass-System-Product-Name kernel: [UFW ALLOW] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=192.168.1.1 LEN=81 TOS=0x00 PREC=0x00 TTL=64 ID=30412 PROTO=UDP SPT=35481 DPT=53 LEN=61 
2025-09-17T15:42:00.661141+03:00 eliass-System-Product-Name kernel: [UFW ALLOW] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=185.26.182.112 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=44198 DF PROTO=TCP SPT=41284 DPT=443 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:00.725141+03:00 eliass-System-Product-Name kernel: [UFW ALLOW] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=239.255.255.250 LEN=193 TOS=0x00 PREC=0x00 TTL=1 ID=23407 DF PROTO=UDP SPT=33794 DPT=1900 LEN=173 
2025-09-17T15:42:01.726147+03:00 eliass-System-Product-Name kernel: [UFW ALLOW] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=239.255.255.250 LEN=193 TOS=0x00 PREC=0x00 TTL=1 ID=24355 DF PROTO=UDP SPT=33794 DPT=1900 LEN=173 
2025-09-17T15:42:03.445138+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=01:00:5e:00:00:fb:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39146 PROTO=2 
2025-09-17T15:42:20.649146+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35190 DF PROTO=TCP SPT=54471 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:20.649152+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35190 DF PROTO=TCP SPT=54471 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:20.650138+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35191 DF PROTO=TCP SPT=54472 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:20.957139+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35192 DF PROTO=TCP SPT=54473 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:21.673139+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35193 DF PROTO=TCP SPT=54471 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:21.673145+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35194 DF PROTO=TCP SPT=54472 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:21.981140+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35195 DF PROTO=TCP SPT=54473 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:23.721140+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35196 DF PROTO=TCP SPT=54471 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:23.722149+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35197 DF PROTO=TCP SPT=54472 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:23.926138+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35198 DF PROTO=TCP SPT=54473 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:27.715156+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35199 DF PROTO=TCP SPT=54471 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:27.715165+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35200 DF PROTO=TCP SPT=54472 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:27.920138+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35201 DF PROTO=TCP SPT=54473 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:35.190143+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=172.64.148.235 LEN=80 TOS=0x00 PREC=0x00 TTL=64 ID=15241 DF PROTO=TCP SPT=44034 DPT=443 WINDOW=477 RES=0x00 ACK PSH URGP=0 
2025-09-17T15:42:35.702138+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35202 DF PROTO=TCP SPT=54471 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:35.702142+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35203 DF PROTO=TCP SPT=54472 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:35.907136+03:00 eliass-System-Product-Name kernel: [UFW BLOCK] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:b4:b5:b6:79:24:7f:08:00 SRC=192.168.1.231 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=35204 DF PROTO=TCP SPT=54473 DPT=9090 WINDOW=64240 RES=0x00 SYN URGP=0 
2025-09-17T15:42:44.913144+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=35.190.80.1 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36215 DF PROTO=TCP SPT=51294 DPT=443 WINDOW=496 RES=0x00 ACK URGP=0 
2025-09-17T15:42:44.928143+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:c0:25:2f:6f:0b:45:08:00 SRC=35.190.80.1 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=119 ID=57359 PROTO=TCP SPT=443 DPT=51294 WINDOW=1042 RES=0x00 ACK URGP=0 
2025-09-17T15:42:50.449148+03:00 eliass-System-Product-Name kernel: [UFW ALLOW] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=192.168.1.1 LEN=68 TOS=0x00 PREC=0x00 TTL=64 ID=22108 PROTO=UDP SPT=34056 DPT=53 LEN=48 
2025-09-17T15:42:50.449159+03:00 eliass-System-Product-Name kernel: [UFW ALLOW] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=192.168.1.1 LEN=68 TOS=0x00 PREC=0x00 TTL=64 ID=50129 PROTO=UDP SPT=33015 DPT=53 LEN=48 
2025-09-17T15:43:00.499150+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=172.64.155.209 LEN=6992 TOS=0x00 PREC=0x00 TTL=64 ID=26311 DF PROTO=TCP SPT=42322 DPT=443 WINDOW=2224 RES=0x00 ACK PSH URGP=0 
2025-09-17T15:43:00.504142+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:c0:25:2f:6f:0b:45:08:00 SRC=172.64.155.209 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=58 ID=15610 DF PROTO=TCP SPT=443 DPT=42322 WINDOW=12 RES=0x00 ACK URGP=0 
2025-09-17T15:43:09.732149+03:00 eliass-System-Product-Name kernel: [UFW ALLOW] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=192.168.1.1 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=9335 PROTO=UDP SPT=40613 DPT=53 LEN=51 
2025-09-17T15:43:09.732160+03:00 eliass-System-Product-Name kernel: [UFW ALLOW] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=192.168.1.1 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=53724 PROTO=UDP SPT=38243 DPT=53 LEN=51 
2025-09-17T15:43:29.968167+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN= OUT=wlp6s0 SRC=192.168.1.111 DST=35.190.80.1 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36216 DF PROTO=TCP SPT=51294 DPT=443 WINDOW=496 RES=0x00 ACK URGP=0 
2025-09-17T15:43:29.984139+03:00 eliass-System-Product-Name kernel: [UFW AUDIT] IN=wlp6s0 OUT= MAC=18:93:41:60:52:f7:c0:25:2f:6f:0b:45:08:00 SRC=35.190.80.1 DST=192.168.1.111 LEN=52 TOS=0x00 PREC=0x00 TTL=119 ID=57360 PROTO=TCP SPT=443 DPT=51294 WINDOW=1042 RES=0x00 ACK URGP=0 
