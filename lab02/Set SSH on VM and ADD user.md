
## 2025-09-22 11:37:46
bash
$ sudo apt install -y openssh-server
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
  ncurses-term openssh-sftp-server ssh-import-id
Suggested packages:
  molly-guard monkeysphere ssh-askpass
The following NEW packages will be installed:
  ncurses-term openssh-server openssh-sftp-server ssh-import-id
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 832 kB of archives.
After this operation, 6,743 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 openssh-sftp-server amd64 1:9.6p1-3ubuntu13.14 [37.3 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 openssh-server amd64 1:9.6p1-3ubuntu13.14 [510 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble/main amd64 ncurses-term all 6.4+20240113-1ubuntu2 [275 kB]
Get:4 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 ssh-import-id all 5.11-0ubuntu2.24.04.1 [10.1 kB]
Preconfiguring packages ...
Fetched 832 kB in 0s (2,173 kB/s)
Selecting previously unselected package openssh-sftp-server.
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
(Reading database ... 156461 files and directories currently installed.)
Preparing to unpack .../openssh-sftp-server_1%3a9.6p1-3ubuntu13.14_amd64.deb ...
Unpacking openssh-sftp-server (1:9.6p1-3ubuntu13.14) ...
Selecting previously unselected package openssh-server.
Preparing to unpack .../openssh-server_1%3a9.6p1-3ubuntu13.14_amd64.deb ...
Unpacking openssh-server (1:9.6p1-3ubuntu13.14) ...
Selecting previously unselected package ncurses-term.
Preparing to unpack .../ncurses-term_6.4+20240113-1ubuntu2_all.deb ...
Unpacking ncurses-term (6.4+20240113-1ubuntu2) ...
Selecting previously unselected package ssh-import-id.
Preparing to unpack .../ssh-import-id_5.11-0ubuntu2.24.04.1_all.deb ...
Unpacking ssh-import-id (5.11-0ubuntu2.24.04.1) ...
Setting up openssh-sftp-server (1:9.6p1-3ubuntu13.14) ...
Setting up openssh-server (1:9.6p1-3ubuntu13.14) ...

Creating config file /etc/ssh/sshd_config with new version
Created symlink /etc/systemd/system/sockets.target.wants/ssh.socket → /usr/lib/systemd/system/ssh.socket.

Created symlink /etc/systemd/system/ssh.service.requires/ssh.socket → /usr/lib/systemd/system/ssh.socket.

Setting up ssh-import-id (5.11-0ubuntu2.24.04.1) ...
Setting up ncurses-term (6.4+20240113-1ubuntu2) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for ufw (0.36.2-6) ...
```

## 2025-09-22 11:38:30
bash
$ sudo systemctl enable ssh
```
```
Synchronizing state of ssh.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install enable ssh
Created symlink /etc/systemd/system/sshd.service → /usr/lib/systemd/system/ssh.service.
Created symlink /etc/systemd/system/multi-user.target.wants/ssh.service → /usr/lib/systemd/system/ssh.service.
```

## 2025-09-22 11:39:32
bash
$ sudo systemctl start ssh
```
```
```

## 2025-09-22 11:40:20
bash
$ systemctl status ssh
```
```
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabled; preset: enabled)
     Active: active (running) since Mon 2025-09-22 11:39:32 EEST; 47s ago
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 4547 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 4549 (sshd)
      Tasks: 1 (limit: 11380)
     Memory: 1.2M (peak: 1.7M)
        CPU: 16ms
     CGroup: /system.slice/ssh.service
             └─4549 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

Sep 22 11:39:32 user1-VirtualBox systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Sep 22 11:39:32 user1-VirtualBox sshd[4549]: Server listening on 0.0.0.0 port 22.
Sep 22 11:39:32 user1-VirtualBox sshd[4549]: Server listening on :: port 22.
Sep 22 11:39:32 user1-VirtualBox systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
```

## 2025-09-22 11:41:23
bash
$ sudo ss -tlnp
```
```
State  Recv-Q Send-Q Local Address:Port Peer Address:PortProcess                                                 
LISTEN 0      4096         0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=4549,fd=3),("systemd",pid=1,fd=156))
LISTEN 0      4096      127.0.0.54:53        0.0.0.0:*    users:(("systemd-resolve",pid=516,fd=17))              
LISTEN 0      4096   127.0.0.53%lo:53        0.0.0.0:*    users:(("systemd-resolve",pid=516,fd=15))              
LISTEN 0      4096       127.0.0.1:631       0.0.0.0:*    users:(("cupsd",pid=1204,fd=7))                        
LISTEN 0      4096           [::1]:631          [::]:*    users:(("cupsd",pid=1204,fd=6))                        
LISTEN 0      4096            [::]:22           [::]:*    users:(("sshd",pid=4549,fd=4),("systemd",pid=1,fd=157))
```

## 2025-09-22 11:57:00
bash
$ sudo adduser eliass
```
```
info: Adding user `eliass' ...
info: Selecting UID/GID from range 1000 to 59999 ...
info: Adding new group `eliass' (1001) ...
info: Adding new user `eliass' (1001) with group `eliass (1001)' ...
info: Creating home directory `/home/eliass' ...
info: Copying files from `/etc/skel' ...
New password: 
Retype new password: 
passwd: password updated successfully
Changing the user information for eliass
Enter the new value, or press ENTER for the default
	Full Name []: 	Room Number []: 	Work Phone []: 	Home Phone []: 	Other []: Is the information correct? [Y/n] info: Adding new user `eliass' to supplemental / extra groups `users' ...
info: Adding user `eliass' to group `users' ...
```

## 2025-09-22 11:58:17
bash
$ usermod -aG sudo eliass
```
```
usermod: Permission denied.
usermod: cannot lock /etc/passwd; try again later.
```

## 2025-09-22 11:59:39
bash
$ sudo usermod -aG sudo eliass
```
```
```

## 2025-09-22 11:59:46
bash
$ id eliass
```
```
uid=1001(eliass) gid=1001(eliass) groups=1001(eliass),27(sudo),100(users)
```

## 2025-09-22 12:03:23
```
bash
$ sudo nano /etc/ssh/sshd_config
```
INSIDE (
Port 22
Protocol 2
PermitRootLogin no
PubkeyAuthentication yes
PasswordAuthentication yes
ChallengeResponseAuthentication no
UsePAM yes
X11Forwarding no
AllowTcpForwarding no
AllowAgentForwarding no
ClientAliveInterval 300
ClientAliveCountMax 2
LoginGraceTime 20
MaxAuthTries 3
PermitEmptyPasswords no
AllowUsers eliass
)
```


## 2025-09-22 12:05:30
bash
$ sudo sshd -t
```
```
```

## 2025-09-22 12:05:48
bash
$ sudo systemctl restart ssh
```
```
```

## 2025-09-22 12:06:11
bash
$ journalctl -u ssh -n 20 --no-pager
```
```
Sep 22 11:39:32 user1-VirtualBox systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Sep 22 11:39:32 user1-VirtualBox sshd[4549]: Server listening on 0.0.0.0 port 22.
Sep 22 11:39:32 user1-VirtualBox sshd[4549]: Server listening on :: port 22.
Sep 22 11:39:32 user1-VirtualBox systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
Sep 22 12:05:48 user1-VirtualBox sshd[4549]: Received signal 15; terminating.
Sep 22 12:05:48 user1-VirtualBox systemd[1]: Stopping ssh.service - OpenBSD Secure Shell server...
Sep 22 12:05:48 user1-VirtualBox systemd[1]: ssh.service: Deactivated successfully.
Sep 22 12:05:48 user1-VirtualBox systemd[1]: Stopped ssh.service - OpenBSD Secure Shell server.
Sep 22 12:05:52 user1-VirtualBox systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Sep 22 12:05:52 user1-VirtualBox sshd[6303]: Server listening on 0.0.0.0 port 22.
Sep 22 12:05:52 user1-VirtualBox sshd[6303]: Server listening on :: port 22.
Sep 22 12:05:52 user1-VirtualBox systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
```
