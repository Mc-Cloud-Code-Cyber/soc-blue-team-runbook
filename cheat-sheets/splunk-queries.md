Splunk Search Query Cheat Sheet
| **Category**              | **Query / Syntax**                               | **Description / Example**                   |                                         |
| ------------------------- | ------------------------------------------------ | ------------------------------------------- | --------------------------------------- |
| **Basic Search**          | `index=main error`                               | Search for "error" in the "main" index      |                                         |
|                           | `index=windows sourcetype=WinEventLog:Security`  | All Windows security logs                   |                                         |
|                           | `host=server01`                                  | All events from host server01               |                                         |
| **Time Range**            | `index=main earliest=-24h latest=now`            | Events from the last 24 hours               |                                         |
|                           | `index=firewall earliest=-15m latest=now`        | Last 15 minutes of firewall logs            |                                         |
| **Field Search**          | `index=web status=404`                           | All web logs with HTTP 404 errors           |                                         |
|                           | `index=linux user=root action=fail`              | Failed actions by root user                 |                                         |
| **Top Values**            | \`index=web                                      | top src\_ip\`                               | Top source IP addresses                 |
|                           | \`index=windows                                  | top user\`                                  | Most active users                       |
| **Failed Logins**         | `index=windows EventCode=4625`                   | Failed Windows login attempts               |                                         |
|                           | `index=linux "Failed password"`                  | Linux SSH failed login attempts             |                                         |
| **Successful Logins**     | `index=windows EventCode=4624`                   | Successful Windows logins                   |                                         |
|                           | `index=linux "Accepted password"`                | Successful Linux SSH logins                 |                                         |
| **By Time**               | \`index=firewall                                 | timechart count by action\`                 | Chart firewall actions over time        |
|                           | \`index=web                                      | timechart span=1h count by status\`         | HTTP status code trends by hour         |
| **Specific IP/User**      | `index=web src_ip=1.2.3.4`                       | All logs from source IP 1.2.3.4             |                                         |
|                           | `index=windows user=jsmith`                      | All logs related to user jsmith             |                                         |
| **Combine Filters**       | `index=firewall action=blocked src_ip=10.0.0.5`  | Blocked traffic from specific IP            |                                         |
|                           | `index=windows EventCode=4625 OR EventCode=4624` | Both failed and successful logins           |                                         |
| **Process Creation**      | `index=windows EventCode=4688`                   | Windows process creation events             |                                         |
|                           | `index=sysmon EventCode=1`                       | Sysmon process creation                     |                                         |
| **Command Line Search**   | `index=sysmon CommandLine="*powershell*"`        | Processes with 'powershell' in command line |                                         |
| **Network Connections**   | `index=windows EventCode=5156`                   | Windows allowed network connections         |                                         |
|                           | `index=sysmon EventCode=3`                       | Sysmon network connection logs              |                                         |
| **Malware/Threats**       | `index=malware signature=*ransom*`               | Malware logs mentioning 'ransom'            |                                         |
|                           | `index=ids alert.signature="*"`                  | All IDS/IPS alerts                          |                                         |
| **File Changes**          | `index=linux "deleted file"`                     | Log events about file deletion              |                                         |
|                           | `index=windows EventCode=4663`                   | File object access in Windows               |                                         |
| **Alerts/Notable Events** | `index=notables severity=high`                   | High severity alerts                        |                                         |
|                           | `index=alerts status!=resolved`                  | All open alerts                             |                                         |
| **Aggregations & Stats**  | \`index=web                                      | stats count by user, src\_ip\`              | Count events by user and IP             |
|                           | \`index=firewall                                 | stats count by action, dest\_port\`         | Firewall actions by port                |
| **Visualization**         | \`index=web                                      | timechart count by status\`                 | Chart HTTP status code counts over time |
|                           | \`index=windows                                  | top limit=10 process\_name\`                | Top 10 processes                        |
