````markdown
## 2025-09-22 10:56:24
```bash
$ ip -br a
````

```
lo               UNKNOWN        127.0.0.1/8 ::1/128 
enp9s0           DOWN           
wlp6s0           UP             192.168.1.111/24 fe80::b607:8687:782c:7470/64 
```

## AFTER STATIC IP AND SSH SETTING ON VM

## 2025-09-22 12:08:58

```bash
$ ssh eliass@192.168.1.150
```

```
Warning: Permanently added '192.168.1.150' (ED25519) to the list of known hosts.
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.14.0-29-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

11 additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
```

## 2025-09-22 12:15:13

```bash
$ ssh-keygen -t ed25519 -a 100 -C eliass-lab
```

```
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/eliass/.ssh/id_ed25519): 
Enter passphrase (empty for no passphrase): Created directory '/home/eliass/.ssh'.

Enter same passphrase again: 
Your identification has been saved in /home/eliass/.ssh/id_ed25519
Your public key has been saved in /home/eliass/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:a2J0Mu9qAnTvAKv8oPEd07A+AM8ISymSPO+oDhVJ658 eliass-lab
The key's randomart image is:
+--[ED25519 256]--+
|  .              |
| . o             |
|..=              |
|**o..            |
|=B=+..+ S        |
|o.*o.*.= .       |
|+oooEo+ +        |
|+=.+o+o+         |
|=.o.o+...        |
+----[SHA256]-----+
```

## 2025-09-22 12:16:44

```bash
$ ssh-copy-id eliass@192.168.1.150
```

```
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/eliass/.ssh/id_ed25519.pub"

The authenticity of host '192.168.1.150 (192.168.1.150)' can't be established.
ED25519 key fingerprint is SHA256:x+RBJzBSkyN1UdO2dHEZEbQblQzpobQRJXa/mA0iII8.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes

/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys

eliass@192.168.1.150's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'eliass@192.168.1.150'"
and check to make sure that only the key(s) you wanted were added.
```

## 2025-09-22 12:17:36

```bash
$ ssh eliass@192.168.1.150
```

```
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.14.0-29-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

11 additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm

Last login: Mon Sep 22 12:09:14 2025 from 192.168.1.111

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
```

## 2025-09-22 12:23:49

```bash
$ sshd -t
```

```
sshd: no hostkeys available -- exiting.
```

## 2025-09-22 12:23:57

```bash
$ sudo sshd -t
```

```
```

## 2025-09-22 12:24:11

```bash
$ sudo systemctl restart ssh
```

```
```

## 2025-09-22 12:24:33

```bash
$ ssh eliass@192.168.1.150
```

```
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.14.0-29-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

11 additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm

Last login: Mon Sep 22 12:17:37 2025 from 192.168.1.150
```

## 2025-09-22 12:25:00

```bash
$ ssh root@192.168.1.150
```

```
root@192.168.1.150: Permission denied (publickey).
```

## 2025-09-22 12:26:00

```bash
$ sudo ufw default deny incoming
```

```
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)
```

## 2025-09-22 12:26:32

```bash
$ sudo ufw default allow outgoing
```

```
Default outgoing policy changed to 'allow'
(be sure to update your rules accordingly)
```

## 2025-09-22 12:27:41

```bash
$ sudo ufw enable
```

```
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
Firewall is active and enabled on system startup
```

## 2025-09-22 12:28:00

```bash
$ sudo ufw status verbouse
```

```
ERROR: Invalid syntax
…
(status verbose → верный вариант)
```

## 2025-09-22 12:28:15

```bash
$ sudo ufw status verbose
```

```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp (OpenSSH)           ALLOW IN    Anywhere
22/tcp (OpenSSH (v6))      ALLOW IN    Anywhere (v6)
```

```
logout
Connection to 192.168.1.150 closed.
```

```
```

