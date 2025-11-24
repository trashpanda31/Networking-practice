# 🌐 Networking Labs  

Welcome to my collection of **networking lab assignments**.  
Each lab covers a specific topic - from launching a simple web server and configuring a firewall 🛡,  
to working with more advanced tools and network scenarios ⚙️.  
In this README you’ll find **short summaries** of what was done and what each lab taught.
### Full logs of executed commands and their outputs are available in each lab’s corresponding folder.  

## Lab 1 - 🔥 Basics of Network Interaction  
* Launched a simple Python HTTP server (`python3 -m http.server 9090`) to understand how services run on a host  
* Verified availability locally and remotely (curl, browser, ping, ss) to practice connectivity checks  
* Configured UFW rules (allow/deny, logging) and explored how firewall policies affect access  
* Analyzed UFW logs in real time to see how allowed and denied traffic is recorded  

## Lab 2 - 🔑 SSH Setup and VM Networking  
* Assigned a static IP (`192.168.1.150`) with Netplan for stable VM networking  
* Installed and configured OpenSSH, tested login with both password and SSH keys  
* Created and configured a sudo-enabled user to handle administrative tasks securely  
* Enabled UFW with default-deny, allowing only SSH to harden remote access  
* Edited and validated `sshd_config` (no root login, key auth) to enforce safer SSH policies  

## Lab 3 - 🌐 Local DNS with dnsmasq  
* Installed and configured `dnsmasq` as a lightweight DNS server on VM (192.168.1.150)  
* Added custom records: `app.lab.test > 192.168.1.200`, `db.lab.test > 192.168.1.201`  
* Verified name resolution with `dig`, `nslookup`, and `ping` from both VM and host  
* Resolved port conflicts with `systemd-resolved` and configured upstream DNS (1.1.1.1, 8.8.8.8)  
* Tested local overrides (`/etc/hosts`) and confirmed dnsmasq takes priority in resolution  
* Ensured custom domains resolve correctly even when external DNS is queried  

## Lab 4 - 📡 DHCP Server and Client on VMs  
* Configured VM1 with two interfaces:  
    * enp0s3 - static IP for SSH (192.168.1.150)  
    * enp0s8 - static IP for Host-Only network (192.168.56.10)  
* Installed and configured `isc-dhcp-server` to serve addresses on enp0s8  
* Defined subnet 192.168.56.0/24 with range 192.168.56.50–100, gateway, and DNS options  
* Restarted the service and confirmed it was running on enp0s8  
* Connected VM2 to Host-Only network > received IP `192.168.56.50` from VM1  
* Verified DHCP process in logs `journalctl -u isc-dhcp-server -f` and checked active leases

![Lab 4 DHCP diagram](https://i.imgur.com/mqwgZIP.png)

## Lab 5 — 🔀 VM1 as SNAT Router for VM2 & VM3
* Continued from **Lab 4**, keeping VM1 as DHCP server for subnet `192.168.56.0/24`.  
* Configured VM1 with two interfaces:  
    * `enp0s3` (WAN) > `192.168.1.150`  
    * `enp0s8` (LAN) > `192.168.56.10`  
* DHCP served range `192.168.56.50–100` with gateway `192.168.56.10` and DNS `1.1.1.1, 8.8.8.8`.  
* Enabled routing by setting `net.ipv4.ip_forward=1`.  
* Applied **SNAT (MASQUERADE)** on `enp0s3` and configured forwarding rules to pass LAN traffic outward.  
* Connected VM2 and VM3 to the LAN > both received IPs via DHCP (`192.168.56.50`, `192.168.56.51`).  
* Verified Internet access from VM2/VM3 (ping to `8.8.8.8`, DNS resolution for `google.com`).  
* Checked DHCP leases and SNAT rules to confirm proper address assignment and traffic masquerading.  

![Lab 5 VM1 as SNAT Router](https://i.imgur.com/9cxz4lK.png)

## Lab 6 - 🔗 VM2 to VM3 via VM1 as SNAT Router  
* Continued from **Lab 4** (DHCP server on VM1) and **Lab 5** (SNAT routing).  
* VM1 kept its role as DHCP + SNAT router:  
    * WAN (`enp0s3` > `192.168.1.150`)  
    * LAN (`enp0s8` > `192.168.56.10`, DHCP range `192.168.56.50–100`).  
* VM2 (client) received IP `192.168.56.50` via DHCP and used VM1 as gateway.  
* VM3 (server) was placed in the external network with static IP `192.168.1.200`.  
* Installed and started **nginx** on VM3 to serve a test page.  
* From VM2, accessed VM3 through VM1:  
    * `ping` and `traceroute` confirmed routing via VM1  
    * `curl http://192.168.1.200` showed nginx welcome page.  
* Verified SNAT rules and DHCP leases on VM1 to confirm proper traffic forwarding.

![Lab 6 — VM2 > VM3 via VM1 (SNAT)](https://i.imgur.com/oj3gRhZ.png)

## 📌 Summary
Across these labs I practiced:
* Running and securing core network services such as **HTTP, SSH, DNS, and DHCP**, learning how to configure, test, and troubleshoot them in real VM environments.  
* Setting up **routing, firewall rules, and source NAT (SNAT/MASQUERADE)**, which provided hands-on understanding of how traffic flows between LAN and WAN segments.  
* Designing and testing **multi-VM network topologies**, where clients obtained IPs via DHCP, resolved domains locally, and accessed external servers through a SNAT gateway.  
* Analyzing logs and packet captures (`ss`, `tcpdump`, `journalctl`), which helped to confirm configurations and understand real packet-level behavior.  
* Gradually combining individual components into a working end-to-end setup, simulating how real networks are built and maintained.  

These experiments gave me a strong foundation in **Linux networking basics, troubleshooting, and secure system configuration**, as well as practical skills for building small but realistic network infrastructures.

