Linux Command Cheat Sheet for SOC Blue Team
Basic Navigation
pwd — Print working directory
ls -alh — List files (long format, human-readable)
cd /path/dir — Change directory
find . -name "*.log" — Find files by name

User & Process Management
whoami — Current user
id — User and group info
ps aux — All running processes
top — Real-time process list
htop — Improved process viewer (may require install)
kill -9 PID — Force kill a process by PID

File & Directory Operations
cat file.txt — Show file contents
less file.txt — View file contents (scroll)
tail -n 100 file.log — Last 100 lines of file
head -n 20 file.log — First 20 lines of file
grep "pattern" file — Search for pattern in file
cp src dest — Copy file
mv old new — Move/rename file
rm file.txt — Delete file

Network Commands
ifconfig — Show network interfaces (legacy)
ip a — Show interfaces (modern)
ping 8.8.8.8 — Test network connectivity
netstat -tuln — Show listening ports (may require install)
ss -tuln — Show listening ports (modern)
lsof -i — List open ports/services
curl ifconfig.me — External IP address

Disk Usage & System Info
df -h — Disk space usage (human readable)
du -sh /path — Size of directory
free -h — RAM usage
uname -a — System/kernel info
uptime — System uptime/load
dmesg | tail — Latest kernel/system messages

Log Analysis
less /var/log/syslog — View system log (Debian/Ubuntu)
less /var/log/messages — View system log (RHEL/CentOS)
journalctl -xe — Systemd logs (modern)
grep "ERROR" /var/log/app.log — Search for errors in logs

File Permissions & Ownership
ls -l — Show permissions
chmod 644 file.txt — Set permissions (rw-r--r--)
chown user:group file — Change owner/group

Useful One-Liners
grep -ir "keyword" /var/log — Case-insensitive search in logs
find / -type f -mtime -1 — Files changed in last 1 day
awk '{print $1,$2}' file.txt — Print first two columns of file

Incident Response
last — Last logins
w — Who is logged in now
history — Bash command history
sudo su — Switch to root (if permitted)

Package Management

Debian/Ubuntu:
sudo apt update && sudo apt upgrade
sudo apt install package

RHEL/CentOS:
sudo yum update
sudo yum install package
