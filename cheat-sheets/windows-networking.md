Windows Networking Command Cheat Sheet
| **Category**                | **Command / Syntax**                                                       | **Description / Example**                              |
| --------------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------ |
| **IP & Interface**          | `ipconfig`                                                                 | Show IP address, subnet, and gateway for all adapters  |
|                             | `ipconfig /all`                                                            | Detailed IP and adapter info, including MAC and DNS    |
|                             | `getmac`                                                                   | Show MAC addresses of all network adapters             |
|                             | `hostname`                                                                 | Show computer name                                     |
| **Connection Tests**        | `ping 8.8.8.8`                                                             | Test connectivity to Google DNS                        |
|                             | `tracert google.com`                                                       | Trace route to google.com                              |
|                             | `pathping 8.8.8.8`                                                         | Trace and analyze path, combines ping & tracert        |
|                             | `nslookup example.com`                                                     | Resolve DNS for a domain                               |
|                             | `Resolve-DnsName example.com` *(PowerShell)*                               | DNS lookup (PowerShell)                                |
| **Open Ports & Sockets**    | `netstat -ano`                                                             | Show all connections, listening ports, and owning PIDs |
|                             | `netstat -rn`                                                              | Show routing table                                     |
|                             | `Get-NetTCPConnection` *(PowerShell)*                                      | List TCP connections (PowerShell 3.0+)                 |
|                             | `Get-NetUDPEndpoint` *(PowerShell)*                                        | List UDP endpoints (PowerShell 3.0+)                   |
| **Network Services**        | `arp -a`                                                                   | Display ARP cache                                      |
|                             | `route print`                                                              | Show IP routing table                                  |
|                             | `nbtstat -n`                                                               | Show NetBIOS local names                               |
|                             | `net view \\hostname`                                                      | List shared resources on another host                  |
|                             | `net use`                                                                  | List network connections and mapped drives             |
| **Wireless**                | `netsh wlan show profiles`                                                 | Show all saved WiFi profiles                           |
|                             | `netsh wlan show interfaces`                                               | Show wireless adapter status                           |
|                             | `netsh wlan show networks`                                                 | List available wireless networks                       |
| **Firewall**                | `netsh advfirewall show allprofiles`                                       | Show firewall status for all profiles                  |
|                             | `netsh firewall show state`                                                | Show firewall state (legacy)                           |
|                             | `Get-NetFirewallRule` *(PowerShell)*                                       | List firewall rules (PowerShell 3.0+)                  |
| **Sharing & SMB**           | `net share`                                                                | List all shared folders                                |
|                             | `net use Z: \\server\share`                                                | Map network share to drive letter Z                    |
| **Bandwidth & Traffic**     | `taskmgr`                                                                  | Open Task Manager (network tab for usage stats)        |
|                             | `perfmon`                                                                  | Open Performance Monitor                               |
|                             | `Resource Monitor` *(resmon.exe)*                                          | View detailed network activity and usage               |
| **Adapters & Drivers**      | `devmgmt.msc`                                                              | Open Device Manager                                    |
|                             | `netsh interface show interface`                                           | Show all network interfaces                            |
|                             | `ipconfig /release`                                                        | Release DHCP IP address                                |
|                             | `ipconfig /renew`                                                          | Renew DHCP IP address                                  |
| **Utilities & Diagnostics** | `winver`                                                                   | Show Windows version info                              |
|                             | `systeminfo`                                                               | Detailed system info, including network adapters       |
|                             | `msinfo32`                                                                 | System Information utility                             |
|                             | `dxdiag`                                                                   | DirectX diagnostics (includes network tab)             |
|                             | `network troubleshooter` *(msdt.exe /id NetworkDiagnosticsNetworkAdapter)* | Launches network troubleshooter                        |
| **Help & Documentation**    | `command /?`                                                               | Show help for any command, e.g. `netstat /?`           |
|                             | `Get-Help Get-NetIPConfiguration` *(PowerShell)*                           | PowerShell help for command                            |
