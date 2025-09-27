# 🌐 Networking Labs  

Welcome to my collection of **networking lab assignments**.  
Each lab covers a specific topic — from launching a simple web server and configuring a firewall 🛡,  
to working with more advanced tools and network scenarios ⚙️.  
In this README you’ll find **short summaries** of what was done and what each lab taught.
### Full logs of executed commands and their outputs are available in each lab’s corresponding folder.  

## Lab 1 — 🔥 Basics of Network Interaction  
* Launched a simple Python HTTP server (`python3 -m http.server 9090`) to understand how services run on a host  
* Verified availability locally and remotely (curl, browser, ping, ss) to practice connectivity checks  
* Configured UFW rules (allow/deny, logging) and explored how firewall policies affect access  
* Analyzed UFW logs in real time to see how allowed and denied traffic is recorded  

## Lab 2 — 🔑 SSH Setup and VM Networking  
* Assigned a static IP (`192.168.1.150`) with Netplan for stable VM networking  
* Installed and configured OpenSSH, tested login with both password and SSH keys  
* Created and configured a sudo-enabled user to handle administrative tasks securely  
* Enabled UFW with default-deny, allowing only SSH to harden remote access  
* Edited and validated `sshd_config` (no root login, key auth) to enforce safer SSH policies  

## Lab 3 — 🌐 Local DNS with dnsmasq  
* Installed and configured `dnsmasq` as a lightweight DNS server on VM (192.168.1.150)  
* Added custom records: `app.lab.test → 192.168.1.200`, `db.lab.test → 192.168.1.201`  
* Verified name resolution with `dig`, `nslookup`, and `ping` from both VM and host  
* Resolved port conflicts with `systemd-resolved` and configured upstream DNS (1.1.1.1, 8.8.8.8)  
* Tested local overrides (`/etc/hosts`) and confirmed dnsmasq takes priority in resolution  
* Ensured custom domains resolve correctly even when external DNS is queried  

## Lab 4 — 📡 DHCP Server and Client on VMs  
* Configured VM1 with two interfaces:  
    * enp0s3 — static IP for SSH (192.168.1.150)  
    * enp0s8 — static IP for Host-Only network (192.168.56.10)  
* Installed and configured `isc-dhcp-server` to serve addresses on enp0s8  
* Defined subnet 192.168.56.0/24 with range 192.168.56.50–100, gateway, and DNS options  
* Restarted the service and confirmed it was running on enp0s8  
* Connected VM2 to Host-Only network → received IP `192.168.56.50` from VM1  
* Verified DHCP process in logs `journalctl -u isc-dhcp-server -f` and checked active leases

![Lab 4 DHCP diagram](https://i.imgur.com/mqwgZIP.png)
