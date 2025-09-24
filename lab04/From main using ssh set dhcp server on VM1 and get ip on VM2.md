## 2025-09-24 13:25:25

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

Last login: Wed Sep 24 13:20:37 2025 from 192.168.1.111
```

## 2025-09-24 13:27:52

```bash
$ ls -l /etc/netplan
```

```
total 12
-rw-r--r-- 1 root root 252 Sep 22 11:15 01-network-manager-all.yaml.bak
-rw-r--r-- 1 root root 251 Sep 22 11:10 01-network-manager-all.yaml.save
-rw------- 1 root root 228 Sep 22 11:28 50-cloud-init.yaml
```

## 2025-09-24 13:30:43

```bash
$ sudo nano /etc/netplan/50-cloud-init.yaml
```

```
INSIDE:
(
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp0s3:
      addresses:
      - "192.168.1.150/24"
      nameservers:
        addresses:
        - 1.1.1.1
        - 8.8.8.8
      dhcp4: false
      routes:
      - to: "0.0.0.0/0"
        via: "192.168.1.1"
    enp0s8:
      renderer: networkd
      dhcp4: false
      addresses: [192.168.56.10/24]
)
```

## 2025-09-24 14:55:34

```bash
$ sudo netplan apply
```

## 2025-09-24 14:55:43

```bash
$ ip -br a
```

```
lo               UNKNOWN        127.0.0.1/8 ::1/128 
enp0s3           UP             192.168.1.150/24 fe80::a00:27ff:feb1:1e94/64 
enp0s8           UP             192.168.56.10/24 fe80::a00:27ff:fe8e:b80c/64 
```

## 2025-09-24 14:57:19

```bash
$ sudo apt install isc-dhcp-server -y
```

```
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Reading package lists...
Building dependency tree...
Reading state information...
The following package was automatically installed and is no longer required:
  libllvm19
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  isc-dhcp-common
Suggested packages:
  isc-dhcp-server-ldap policycoreutils
The following NEW packages will be installed:
  isc-dhcp-common isc-dhcp-server
0 upgraded, 2 newly installed, 0 to remove and 19 not upgraded.
Need to get 1,281 kB of archives.
After this operation, 4,281 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble/universe amd64 isc-dhcp-server amd64 4.4.3-P1-4ubuntu2 [1,236 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble/universe amd64 isc-dhcp-common amd64 4.4.3-P1-4ubuntu2 [45.8 kB]
Preconfiguring packages ...
Fetched 1,281 kB in 0s (3,223 kB/s)
Selecting previously unselected package isc-dhcp-server.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 159387 files and directories currently installed.)
Preparing to unpack .../isc-dhcp-server_4.4.3-P1-4ubuntu2_amd64.deb ...
Unpacking isc-dhcp-server (4.4.3-P1-4ubuntu2) ...
Selecting previously unselected package isc-dhcp-common.
Preparing to unpack .../isc-dhcp-common_4.4.3-P1-4ubuntu2_amd64.deb ...
Unpacking isc-dhcp-common (4.4.3-P1-4ubuntu2) ...
Setting up isc-dhcp-server (4.4.3-P1-4ubuntu2) ...
Generating /etc/default/isc-dhcp-server...
Created symlink /etc/systemd/system/multi-user.target.wants/isc-dhcp-server.service → /usr/lib/systemd/system/isc-dhcp-server.service.

Created symlink /etc/systemd/system/multi-user.target.wants/isc-dhcp-server6.service → /usr/lib/systemd/system/isc-dhcp-server6.service.

Setting up isc-dhcp-common (4.4.3-P1-4ubuntu2) ...
Processing triggers for man-db (2.12.0-4build2) ...
```

## 2025-09-24 14:59:43

```bash
$ sudo nano /etc/default/isc-dhcp-server
```

```
INSIDE NANO:
(
INTERFACESv4:"" > INTERFACESv4="enp0s8"
)
```

## 2025-09-24 15:01:12

```bash
$ sudo nano /etc/dhcp/dhcpd.conf
```

```
INSIDE NANO:
(
subnet 192.168.56.0 netmask 255.255.255.0 {
  range 192.168.56.50 192.168.56.100;   
  option routers 192.168.56.10;         
  option domain-name-servers 1.1.1.1, 8.8.8.8;
  default-lease-time 600;
  max-lease-time 7200;
}
)
```

## 2025-09-24 15:05:10

```bash
$ sudo systemctl restart isc-dhcp-server
```

## 2025-09-24 15:05:40

```bash
$ sudo systemctl status isc-dhcp-server
```

```
● isc-dhcp-server.service - ISC DHCP IPv4 server
     Loaded: loaded (/usr/lib/systemd/system/isc-dhcp-server.service; enabled; preset: enabled)
     Active: active (running) since Wed 2025-09-24 15:05:10 EEST; 29s ago
       Docs: man:dhcpd(8)
   Main PID: 16828 (dhcpd)
      Tasks: 1 (limit: 11380)
     Memory: 3.7M (peak: 4.3M)
        CPU: 7ms
     CGroup: /system.slice/isc-dhcp-server.service
             └─16828 dhcpd -user dhcpd -group dhcpd -f -4 -pf /run/dhcp-server/dhcpd.pid -cf /etc/dhcp/dhcpd.conf enp0s8

Sep 24 15:05:10 user1-VirtualBox dhcpd[16828]: PID file: /run/dhcp-server/dhcpd.pid
Sep 24 15:05:10 user1-VirtualBox dhcpd[16828]: Wrote 0 leases to leases file.
Sep 24 15:05:10 user1-VirtualBox sh[16828]: Wrote 0 leases to leases file.
Sep 24 15:05:10 user1-VirtualBox dhcpd[16828]: Listening on LPF/enp0s8/08:00:27:8e:b8:0c/192.168.56.0/24
Sep 24 15:05:10 user1-VirtualBox sh[16828]: Listening on LPF/enp0s8/08:00:27:8e:b8:0c/192.168.56.0/24
Sep 24 15:05:10 user1-VirtualBox sh[16828]: Sending on   LPF/enp0s8/08:00:27:8e:b8:0c/192.168.56.0/24
Sep 24 15:05:10 user1-VirtualBox sh[16828]: Sending on   Socket/fallback/fallback-net
Sep 24 15:05:10 user1-VirtualBox dhcpd[16828]: Sending on   LPF/enp0s8/08:00:27:8e:b8:0c/192.168.56.0/24
Sep 24 15:05:10 user1-VirtualBox dhcpd[16828]: Sending on   Socket/fallback/fallback-net
Sep 24 15:05:10 user1-VirtualBox dhcpd[16828]: Server starting service.
```

## Enable VM2 with Host-Only, VM2 got an IP from DHCP.

## 2025-09-24 15:32:20

```bash
$ cat /var/lib/dhcp/dhcpd.leases
```

```
# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-4.4.3-P1

# authoring-byte-order entry is generated, DO NOT DELETE
authoring-byte-order little-endian;

server-duid "\000\001\000\0010f\232\366\010\000'\216\270\014";

lease 192.168.56.50 {
  starts 3 2025/09/24 12:08:03;
  ends 3 2025/09/24 12:18:03;
  cltt 3 2025/09/24 12:08:03;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 08:00:27:a5:b8:87;
  uid "\001\010\000'\245\270\207";
  client-hostname "ubuntu";
}
lease 192.168.56.50 {
  starts 3 2025/09/24 12:11:38;
  ends 3 2025/09/24 12:21:38;
  cltt 3 2025/09/24 12:11:38;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 08:00:27:a5:b8:87;
  uid "\001\010\000'\245\270\207";
  client-hostname "ubuntu";
}
lease 192.168.56.50 {
  starts 3 2025/09/24 12:20:40;
  ends 3 2025/09/24 12:30:40;
  cltt 3 2025/09/24 12:20:40;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 08:00:27:a5:b8:87;
  uid "\001\010\000'\245\270\207";
  client-hostname "ubuntu";
}
lease 192.168.56.50 {
  starts 3 2025/09/24 12:21:25;
  ends 3 2025/09/24 12:31:25;
  cltt 3 2025/09/24 12:21:25;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 08:00:27:a5:b8:87;
  uid "\001\010\000'\245\270\207";
  client-hostname "user2-VirtualBox2";
}
lease 192.168.56.50 {
  starts 3 2025/09/24 12:31:13;
  ends 3 2025/09/24 12:41:13;
  cltt 3 2025/09/24 12:31:13;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 08:00:27:a5:b8:87;
  uid "\001\010\000'\245\270\207";
  client-hostname "user2-VirtualBox2";
}
```

## 2025-09-24 15:34:31

```bash
$ sudo journalctl -u isc-dhcp-server -f
```

```
Sep 24 15:21:25 user1-VirtualBox dhcpd[16828]: DHCPREQUEST for 192.168.56.50 (192.168.56.10) from 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 24 15:21:25 user1-VirtualBox dhcpd[16828]: DHCPACK on 192.168.56.50 to 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 24 15:21:27 user1-VirtualBox dhcpd[16828]: reuse_lease: lease age 2 (secs) under 25% threshold, reply with unaltered, existing lease for 192.168.56.50
Sep 24 15:21:27 user1-VirtualBox dhcpd[16828]: DHCPREQUEST for 192.168.56.50 from 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 24 15:21:27 user1-VirtualBox dhcpd[16828]: DHCPACK on 192.168.56.50 to 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 24 15:23:53 user1-VirtualBox dhcpd[16828]: reuse_lease: lease age 148 (secs) under 25% threshold, reply with unaltered, existing lease for 192.168.56.50
Sep 24 15:23:53 user1-VirtualBox dhcpd[16828]: DHCPREQUEST for 192.168.56.50 from 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 24 15:23:53 user1-VirtualBox dhcpd[16828]: DHCPACK on 192.168.56.50 to 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 24 15:31:13 user1-VirtualBox dhcpd[16828]: DHCPREQUEST for 192.168.56.50 from 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 24 15:31:13 user1-VirtualBox dhcpd[16828]: DHCPACK on 192.168.56.50 to 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 24 15:36:14 user1-VirtualBox dhcpd[16828]: DHCPREQUEST for 192.168.56.50 from 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
Sep 24 15:36:14 user1-VirtualBox dhcpd[16828]: DHCPACK on 192.168.56.50 to 08:00:27:a5:b8:87 (user2-VirtualBox2) via enp0s8
```

```
```

