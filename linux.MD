## Networking
`ping google.com` - test connection  
`curl -I https://google.com` - test connection  
`telnet hostname port` - test connection  
`nslookup google.com` - translates domain name to IP address  
`ifconfig -a` or `ip addr show` or `hostname -I` - check ip address (In the eth0 check the inet)  
`netstat -tulnp` - open ports  
`cat /etc/services | grep <service>` - check service ports  
`nc -zv hostname port or nmap -p 80,443 hostname` - test if port is open/listening  
`cat /etc/resolv.conf` - check DNS settings  
`echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf` - add public DNS servers to resolv.conf  
`firewall-cmd --permanent --add-port=22/tcp` - add firewall rules  
`sudo firewall-cmd --reload` - apply firewall rule changes without interrupting connections  
`sudo firewall-cmd --list-all` - show all active firewall rules, zones, services, and ports  
`cat /etc/hosts` - check local hostname resolution  

## TLS/SSL Certificates
`curl -v https://example.com` - curl website to see if it has certificate  
`openssl s_client -connect example.com:443 -showcerts` - test SSL connection and view certificate  
`openssl s_client -connect example.com:443 2>/dev/null | openssl x509 -noout -dates` - check certificate expiration  
`ls -la /etc/ssl/certs/ | head -20` view system's trusted CA certificates  
`ls -l /etc/ssl/certs/ca-certificates.crt` - check the CA bundle file  
`update-ca-certificates` - update system CA certificates (scans /usr/local/share/ca-certificates/ for new certificate files)  
`openssl x509 -in certificate.crt -text -noout` - inspect certificate details  
`openssl s_client -showcerts -connect example.com:443 </dev/null | sed -n -e '/^-----BEGIN/,/^-----END/ p' > certificate.cer` - extract a certificate from a live service  
`openssl x509 -in certificate.cer -noout` - validate certificate  
`sudo cp certificate.cer /usr/local/share/ca-certificates/extracted-ca.crt` - copy to the right location (renaming to .crt is a good practice). UPDATE CA-CERTIFICATES after  

## Installing packages
`sudo apt update && sudo apt upgrade -y` - update packages  
`sudo apt install package_name` - install package  
`sudo apt remove package_name` - uninstall package (keeps config files)  

##	Disk usage - Check tasks, CPU, Memory, RAM
`df -h` - check overall disk usage  
`du -ah <folder>` - disk usage in human readable format  
`du -sh <folder>` - total disk usage of a directory  
`free -h` - check memory usage  
`top` or `htop` - system summary  
`ps aux` or `ps aux --sort=-%cpu | head -10` - check running processes  
`kill <PID>` - kill process  
`kill -9 <PID>` - force kill process  
`uname -a` - print system information  
`mount` - show mounted filesystems  
`lsblk` - list all block devices (disks/partitions)  
`sudo mount /dev/xvdf /data` - mount disk to directory  
`sudo umount /data` - unmount filesystem  
`sudo vim /etc/fstab` - mount permanently  

## User/ File permissions and ownership
`who` - who is logged  
`whoami` - system’s username  
`id` - user identification  
`groups` - display all the groups for which the user belongs to  
`users` - displays usernames of all users currently logged on the system  
`adduser <user> passwd <password>` - create user  
`groupadd <group>` - create group  
`sudo usermod -aG sudo <username>`- grant sudo privileges  
`chown user filename` or `chown user:group filename` - changing Ownership and Group  
`chgrp group_name filename` - change group-owner only  
`chmod` for ex `chmode 764 test.txt` - change access  
Read - 4, Write - 2, Execute - 1  
`stat filename` - view detailed file permissions  

## Applications
`cat /etc/nginx/nginx.conf` - check application configuration  
`vim /etc/nginx/conf.d/goapp.conf` - create specific configuration  
`systemctl status <app>` - check application status  
`systemctl start <app>` or `systemctl stop <app>` - start/stop application  
`systemctl enable <app>` - enables a service to start automatically at boot  
`systemctl daemon-reload` - when you modify service configuration files and need systemd to recognize the changes  
`journalctl -u <service_name>` or `journalctl -u <service> -n 50` - check application logs  
`systemctl --type=service | grep -i <application>` - check running services  

# Cronjobs / scripts
`vim ./script.sh` - create script  
`chmod +x ./bcript.sh` - make it executable  
`crontab -e` and put `0 2 * * * /home/yourusername/script.sh` - open cronjob editor  
`crontab -l` - list cronjobs  
`sudo systemctl status cron` - check cron service status  

# Extract and compress tar archive files
`tar -czvf backup.tar.gz /data` - create archive  
`tar -xzvf backup.tar.gz` - extract archive  

## Search/ Copy Files
`grep "^hello" test.txt` or `grep -i "hELLo" text.txt` - search patterns in files  
`find ./directory_name -name file_name` - search file with name  
`find ./test -name test.txt -exec rm -i {} \;` - search file and delete it after confirmation  
`find /home/bob/preserved -name ".*" -type f -exec sudo cp {} /opt/appdata/hidden/ \;` - run command with find  
`grep -R "timeout" /var/log/` - check string in logs  
`sudo sed -i 's/\b<string_to_be_changed>\b/<new_string>/gi' /opt/appdata/*` - text replacements  

## Curl Command
`curl http://example.com` - sends a simple GET request to the specified URL  
`curl -X POST http://example.com` - specifies a request method other than the default GET  
`curl -H "Content-Type: application/json" http://example.com` - includes custom headers in the request  
`curl -X POST --data "key1=value1&key2=value2" http://example.com` - send POST Data: Sends data as POST request payload  

## File and directory commands
`pwd` - current working directory  
`ls` or `ls -la` - list files (including hidden)  
`mkdir` or `mkdir -p dir1/dir2/` - create directories  
`rm` or `rm -r` - delete  
`cd` - change directory  
`touch` - create empty file  
`cat` or `cat filename.txt | head -n 5` - read file  
`cp -r source_dir/ destination_dir/` - copy directory recursively  
`mv oldname newname` - rename or move files  

## SSH
`ssh <host-name> or <ip-address>` - connect remote machine using IP address or machine name  
`ssh username@hostname_or_ip-address` - connect remote machine using username  
`ssh username@hostname_or_ip-address -p port_number` - connect remote machine using custom port  
`ssh-keygen -t rsa` - generate SSH keys using keygen  
`scp fileName user@remotehost:destinationPath` - copy a File Remotely over SSH  
