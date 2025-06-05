Linux Networking Command Cheat Sheet
| **Category**             | **Command / Syntax**              | **Description / Example**                               |
| ------------------------ | --------------------------------- | ------------------------------------------------------- |
| **IP & Interface**       | `ip a`                            | Show all network interfaces and IP addresses            |
|                          | `ifconfig`                        | Show network interface config (may require `net-tools`) |
|                          | `ip link show`                    | List all network interfaces                             |
|                          | `ip addr show eth0`               | Show IP details for interface eth0                      |
|                          | `hostname -I`                     | Show IP address(es) only                                |
| **Network Status**       | `nmcli device status`             | Show NetworkManager device status                       |
|                          | `iwconfig`                        | Show wireless interface info                            |
|                          | `ethtool eth0`                    | Show/change ethernet settings                           |
| **DHCP & DNS**           | `cat /etc/resolv.conf`            | Show DNS configuration                                  |
|                          | `dhclient -v eth0`                | Request IP from DHCP server for eth0                    |
| **Connection Tests**     | `ping 8.8.8.8`                    | ICMP ping Google DNS                                    |
|                          | `traceroute google.com`           | Trace network path to google.com (install if needed)    |
|                          | `mtr 8.8.8.8`                     | Network diagnostics combining ping & traceroute         |
|                          | `nc -zv 192.168.1.10 80`          | Test if port 80 is open on target with netcat           |
| **Open Ports & Sockets** | `netstat -tuln`                   | List listening TCP/UDP ports                            |
|                          | `ss -tuln`                        | Modern socket stats/listening ports                     |
|                          | `lsof -i`                         | List all open network connections                       |
| **Routing**              | `ip route`                        | Show routing table                                      |
|                          | `route -n`                        | Show kernel routing table (legacy)                      |
| **ARP & MAC**            | `ip neigh`                        | Show ARP table                                          |
|                          | `arp -a`                          | Display ARP cache (may require `net-tools`)             |
|                          | `ip link set eth0 up`             | Bring interface eth0 up                                 |
|                          | `ip link set eth0 down`           | Bring interface eth0 down                               |
| **Firewall**             | `ufw status`                      | Show uncomplicated firewall status                      |
|                          | `sudo ufw enable`                 | Enable UFW firewall                                     |
|                          | `sudo ufw allow 22/tcp`           | Allow SSH port 22 through firewall                      |
|                          | `iptables -L`                     | List iptables firewall rules                            |
| **Network Services**     | `systemctl status networking`     | Status of networking service                            |
|                          | `systemctl restart networking`    | Restart networking service                              |
|                          | `systemctl status NetworkManager` | Status of NetworkManager (Ubuntu)                       |
| **Wireless Tools**       | `iwlist scan`                     | Scan for wireless networks                              |
|                          | `nmcli dev wifi`                  | List available WiFi networks                            |
| **Packet Capture**       | `tcpdump -i eth0`                 | Capture packets on eth0                                 |
|                          | `sudo tshark -i eth0`             | CLI version of Wireshark (needs install)                |
| **Bandwidth/Traffic**    | `iftop -i eth0`                   | Real-time bandwidth usage by host (needs install)       |
|                          | `nload`                           | Visualize network traffic (needs install)               |
