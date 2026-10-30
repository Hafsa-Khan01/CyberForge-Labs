# Week 1 — Linux Command Cheat Sheet

| Command | Purpose | Example |
|---|---|---|
| `pwd` | Show current directory | `pwd` |
| `whoami` | Show current user | `whoami` |
| `id` | Show UID, GID and groups | `id` |
| `uname -a` | Kernel/system information | `uname -a` |
| `hostname` | Show host name | `hostname` |
| `ip a` | Show interfaces and addresses | `ip a` |
| `ip route` | Show routing table | `ip route` |
| `ping` | Test reachability | `ping -c 4 <host>` |
| `traceroute` | Show route path | `traceroute <host>` |
| `nslookup` | Query DNS | `nslookup example.com` |
| `dig` | Detailed DNS query | `dig example.com` |
| `ls` | List files | `ls -lah` |
| `cd` | Change directory | `cd /var/log` |
| `mkdir` | Create directory | `mkdir lab` |
| `touch` | Create empty file/update timestamp | `touch notes.txt` |
| `cp` | Copy files | `cp a.txt b.txt` |
| `mv` | Move/rename files | `mv old.txt new.txt` |
| `rm` | Remove files | `rm file.txt` |
| `cat` | Print file contents | `cat notes.txt` |
| `less` | Read long files interactively | `less /var/log/syslog` |
| `head` | Show first lines | `head -n 20 file` |
| `tail` | Show last lines | `tail -n 30 file` |
| `grep` | Search text | `grep -i error app.log` |
| `find` | Find files by criteria | `find /home -name '*.txt'` |
| `chmod` | Change permissions | `chmod 640 file` |
| `chown` | Change owner/group | `sudo chown user:group file` |
| `ps` | List processes | `ps aux` |
| `top` | Live process view | `top` |
| `ss` | Inspect sockets/listeners | `ss -tulpn` |
| `df -h` | Filesystem free space | `df -h` |
| `du -sh` | Directory size | `du -sh /var/log` |
| `free -h` | Memory usage | `free -h` |
| `systemctl` | Inspect/manage services | `systemctl status ssh` |
| `crontab -l` | List current user's cron jobs | `crontab -l` |
| `man` | Open manual page | `man chmod` |

Use commands only on systems you own or are authorized to administer. Check paths carefully before destructive commands.
