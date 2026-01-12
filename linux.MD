## User/ System and Hardware information

`who` - who is logged  
`whoami` - system’s username  
`id` - user identification  
`group` - display all the groups for which the user belongs to  
`users` - Displays usernames of all users currently logged on the system  
`adduser <user> passwd <password>` - create user  
`usermod -aG sudo <user>`- grant sudo  
`uname -a` - print system information  

## File and directory commands

`pwd` - current working directory  
`ls` or `ls -l` - list files  
`mkdir` or `mkdir -p dir1/dir2/` - create directories  
`rm` or `rm -r` - delete  
`cd` - change directory  
`touch` - create empty file  
`cat` or `cat filename.txt | head -n 5` - read file  

## File permissions and ownership

`chmod` for ex `chmode 764 test.txt` - change access  
Read - 4  
Write - 2  
Execute - 1  

`chown user filename` or `chown user:group filename` - changing Ownership and Group  
`chgrp group_name filename` - change group-owner only  

## Networking

`ping google.com` - test connection  
`curl -I https://google.com` - test connection  
`telnet hostname port` - test connection  
`ifconfig -a` or `ip addr show` or `hostname -I` - check ip address (In the eth0 check the inet)  
`netstat -tulnp` - open ports  
`cat /etc/services | grep <service>` - check service ports  
`cat /etc/resolv.conf` - check DNS settings  
`echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf` - add public DNS servers to resolv.conf  

## Installing packages
`sudo apt update && sudo apt upgrade -y` - update packages
`sudo apt install package_name` - install package    
`sudo apt remove package_name` - uninstall package (keeps config files)  

## Disk usage
`df -h` - check overall disk usage  
`du -ah <folder>` - disk usage in human readable format  
`du -sh <folder>` - total disk usage of a directory   

## Search Files
`grep "^hello" test.txt` or `grep -i "hELLo" text.txt` - search patterns in files  
`find ./directory_name -name file_name` - search file with name  
`find ./test -name test.txt -exec rm -i {} \;` - search file and delete it after confirmation  
`grep -R "timeout" /var/log/` - check string in logs  

## SSH
`ssh <host-name> or <ip-address>` - connect remote machine using IP address or machine name  
`ssh username@hostname_or_ip-address` - connect remote machine using username  
`ssh username@hostname_or_ip-address -p port_number` - connect remote machine using custom port  
`ssh-keygen -t rsa` - generate SSH keys using keygen  
`scp fileName user@remotehost:destinationPath` - copy a File Remotely over SSH  

##	Check tasks, CPU, Memory, RAM
`top` - system summary  
`ps aux` or `ps aux --sort=-%cpu | head -10` - check running processes  
`kill <PID>` - kill process 

## Curl Command
`curl http://example.com` - sends a simple GET request to the specified URL  
`curl -X POST http://example.com` - specifies a request method other than the default GET  
`curl -H "Content-Type: application/json" http://example.com` - includes custom headers in the request  
`curl -X POST --data "key1=value1&key2=value2" http://example.com` - send POST Data: Sends data as POST request payload  

## Applications
`systemctl status <app>` - check application status  
`systemctl start <app>` or `systemctl stop <app>` - start/stop application  
`systemctl enable <app>` - enables a service to start automatically at boot  
`systemctl daemon-reload` - when you modify service configuration files and need systemd to recognize the changes  
`journalctl -u <service_name>` or `journalctl -u <service> -n 50` - check application logs  
`systemctl --type=service | grep -i <application>` - check running services  

# Cronjobs
`vim ./script.sh` - create script  
`chmod +x ./bcript.sh` - make it executable  
`crontab -e` and put `0 2 * * * /home/yourusername/script.sh` - open cronjob editor  
`crontab -l` - list cronjobs  

# Extract and compress tar archive files
`tar -czvf backup.tar.gz /data` - create archive  
`tar -xzvf backup.tar.gz` - extract archive  

# Mount additional storage
`lsblk` - list all block devices (disks/partitions)  
`sudo mount /dev/xvdf /data` - mount disk to directory  
`df -h` - verify mount succeeded  
`ls /data` - check mount point  
`sudo vim /etc/fstab` -  mount Permanently  
