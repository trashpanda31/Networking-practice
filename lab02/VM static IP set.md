
## 2025-09-22 11:26:35
bash
$ ip -br a
`````
`````
lo               UNKNOWN        127.0.0.1/8 ::1/128 
enp0s3           UP             192.168.1.202/24 fe80::a00:27ff:feb1:1e94/64 
`````

## 2025-09-22 11:26:49
bash
$ ls -l /etc/netplan/
`````
`````
total 12
-rw-r--r-- 1 root root 252 Sep 22 11:15 01-network-manager-all.yaml.bak
-rw-r--r-- 1 root root 251 Sep 22 11:10 01-network-manager-all.yaml.save
-rw------- 1 root root  65 Sep 17 17:49 50-cloud-init.yaml
`````

## 2025-09-22 11:26:49
bash
$ sudo nano /etc/netplan/50-cloud-init.yaml
INSIDE (
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: no
      addresses:
        - 192.168.1.150/24
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses: [1.1.1.1, 8.8.8.8]
        )
`````
`````


## 2025-09-22 11:31:21
bash
$ sudo netplan try
`````
`````
Do you want to keep these settings?


Press ENTER before the timeout to accept the new configuration


Changes will revert in 120 secondsChanges will revert in 119 secondsChanges will revert in 118 secondsChanges will revert in 117 secondsChanges will revert in 116 secondsChanges will revert in 115 secondsChanges will revert in 114 secondsChanges will revert in 113 seconds
Configuration accepted.
`````

## 2025-09-22 11:31:49
bash
$ ip -br a
`````
`````
lo               UNKNOWN        127.0.0.1/8 ::1/128 
enp0s3           UP             192.168.1.150/24 fe80::a00:27ff:feb1:1e94/64 
`````

## 2025-09-22 11:32:04
bash
$ ip route
`````
`````
default via 192.168.1.1 dev enp0s3 proto static metric 100 
192.168.1.0/24 dev enp0s3 proto kernel scope link src 192.168.1.150 metric 100 
`````
