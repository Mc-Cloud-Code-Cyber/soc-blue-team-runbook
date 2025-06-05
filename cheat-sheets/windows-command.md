Windows Command Cheat Sheet for SOC Blue Team
| **Category**           | **Command**                                                     | **Description / Example**                            |                                 |
| ---------------------- | --------------------------------------------------------------- | ---------------------------------------------------- | ------------------------------- |
| **Navigation**         | `cd \path\to\dir`                                               | Change directory                                     |                                 |
|                        | `dir /a /s`                                                     | List all files (including hidden, subdirectories)    |                                 |
|                        | `tree`                                                          | Show directory structure visually                    |                                 |
|                        | `type file.txt`                                                 | Display file contents                                |                                 |
| **User & Session**     | `whoami`                                                        | Show current user                                    |                                 |
|                        | `net user`                                                      | List all users                                       |                                 |
|                        | `query user`                                                    | List logged-in users                                 |                                 |
|                        | `qwinsta`                                                       | Show all sessions                                    |                                 |
|                        | `logoff [sessionID]`                                            | Log off a user session                               |                                 |
| **Task & Process**     | `tasklist`                                                      | List running processes                               |                                 |
|                        | `taskkill /F /PID 1234`                                         | Force kill process by PID                            |                                 |
|                        | `Get-Process` *(PowerShell)*                                    | List running processes                               |                                 |
|                        | `Get-Service` *(PowerShell)*                                    | List all services                                    |                                 |
|                        | `sc query`                                                      | Service status overview                              |                                 |
| **Network**            | `ipconfig /all`                                                 | Full IP configuration                                |                                 |
|                        | `ping 8.8.8.8`                                                  | Test network connectivity                            |                                 |
|                        | `netstat -ano`                                                  | List all connections, ports, PIDs                    |                                 |
|                        | `Get-NetTCPConnection` *(PowerShell)*                           | List TCP connections                                 |                                 |
|                        | `arp -a`                                                        | Show ARP table                                       |                                 |
|                        | `nslookup domain.com`                                           | DNS lookup                                           |                                 |
|                        | `tracert 8.8.8.8`                                               | Trace network route                                  |                                 |
|                        | `route print`                                                   | Display routing table                                |                                 |
|                        | `netsh advfirewall show allprofiles`                            | Show firewall settings                               |                                 |
| **System Info**        | `systeminfo`                                                    | Display system information                           |                                 |
|                        | `hostname`                                                      | Print computer name                                  |                                 |
|                        | `wmic computersystem get model,name,manufacturer,systemtype`    | Show hardware info                                   |                                 |
|                        | `Get-ComputerInfo` *(PowerShell)*                               | System details                                       |                                 |
|                        | `ver`                                                           | Windows version                                      |                                 |
|                        | `set`                                                           | Show environment variables                           |                                 |
| **File Ops & Search**  | `copy file1.txt D:\backup\`                                     | Copy file                                            |                                 |
|                        | `move file.txt ..\archive\`                                     | Move file                                            |                                 |
|                        | `del /f /s /q *.tmp`                                            | Delete all .tmp files (force, subdirs, quiet)        |                                 |
|                        | `attrib +h file.txt`                                            | Hide file                                            |                                 |
|                        | `icacls C:\file.txt`                                            | Show/change file permissions                         |                                 |
|                        | `findstr /i "error" log.txt`                                    | Search for "error" in log file (case-insensitive)    |                                 |
|                        | \`dir /s /b                                                     | findstr ".log"\`                                     | List all .log files recursively |
| **Log & Event Viewer** | `eventvwr`                                                      | Open Event Viewer GUI                                |                                 |
|                        | `wevtutil qe Security /c:10 /rd:true /f:text`                   | Show last 10 Security log events                     |                                 |
|                        | `Get-EventLog -LogName Security -Newest 20` *(PowerShell)*      | Last 20 security events                              |                                 |
|                        | `Get-WinEvent -LogName Application -MaxEvents 5` *(PowerShell)* | Last 5 app events                                    |                                 |
| **Incident Response**  | `netstat -anob`                                                 | Show ports and owning process (binary)               |                                 |
|                        | `wmic process list brief`                                       | Show brief process info                              |                                 |
|                        | `schtasks /query /fo LIST /v`                                   | List all scheduled tasks                             |                                 |
|                        | `Get-LocalUser` *(PowerShell)*                                  | List local users                                     |                                 |
|                        | `Get-LocalGroupMember Administrators` *(PowerShell)*            | List local admins                                    |                                 |
|                        | `Get-Content C:\Windows\System32\drivers\etc\hosts`             | Show hosts file                                      |                                 |
|                        | `Get-Command` *(PowerShell)*                                    | List all cmdlets                                     |                                 |
| **System Utilities**   | `chkdsk C:`                                                     | Check disk                                           |                                 |
|                        | `sfc /scannow`                                                  | Run System File Checker                              |                                 |
|                        | `diskpart`                                                      | Open disk partition tool                             |                                 |
|                        | `msinfo32`                                                      | System Information utility                           |                                 |
|                        | `compmgmt.msc`                                                  | Computer Management console                          |                                 |
|                        | `regedit`                                                       | Open Registry Editor                                 |                                 |
| **Help & More**        | `help`                                                          | Show help for commands                               |                                 |
|                        | `command /?`                                                    | Show help for specific command (e.g., `ipconfig /?`) |                                 |
|                        | `Get-Help Get-Process` *(PowerShell)*                           | PowerShell help for command                          |                                 |
