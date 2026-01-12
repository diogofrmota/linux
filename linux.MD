## User information

`who` - who is logged  
`whoami` - system’s username  
`id` - user identification  
`group` - display all the groups for which the user belongs to  
`users` - Displays usernames of all users currently logged on the system  


## File and directory commands

`pwd` - current working directory  
`ls` or `ls -l` - list files  
`mkdir` or `mkdir -p dir1/dir2/` - create directories  
`rm` or `rm -r` - delete  
`cd` - change directory  
`touch` - create empty file  
`cat` or `cat filename.txt | head -n 5` - read file  

## File permissions

`chmod` for ex `chmode 764 test.txt` - change access  
Read - 4  
Write - 2  
Execute - 1  

`chown user filename` or `chown user:group filename` - changing Ownership and Group  
`chgrp group_name filename` - change group-owner only  

## Networking

`ifconfig -a` or `ip addr show` or `hostname -I` - check ip address  
`ping` - test connection  
`netstat -tulnp` - open ports  

## Installing packages
`sudo apt install package_name` - install package  
`apt show package_name - package` description  
`sudo apt remove package_name` - uninstall package (keeps config files)  

## Disk usage
`du -ah <folder>` - disk usage in human readable format  
`du -sh <folder>` - total disk usage of a directory  

## System and Hardware information

`uname -a` - print system information  

## Search Files
`grep "^hello" test.txt` or `grep -i "hELLo" text.txt` - search patterns in files  
`find ./directory_name -name file_name` - search file with name  
`find ./test -name test.txt -exec rm -i {} \;` - search file and delete it after confirmation  

## SSH
`ssh <host-name> or <ip-address>` - connect remote machine using IP address or machine name  
`ssh username@hostname_or_ip-address` - connect remote machine using username  
`ssh username@hostname_or_ip-address -p port_number` - connect remote machine using custom port  
`ssh-keygen -t rsa` - generate SSH keys using keygen  
`scp fileName user@remotehost:destinationPath` - copy a File Remotely over SSH  

##	Vi/Vim-commands
`vim <filename>` or `vi <filename>` - start with Editor  

##	Top/TaskManager Command
`top` - system summary  

## Kill Command
`kill <PID>` - kill process  

## Curl Command
`curl http://example.com` - sends a simple GET request to the specified URL  
`curl -X POST http://example.com` - specifies a request method other than the default GET  
`curl -H "Content-Type: application/json" http://example.com` - includes custom headers in the request  
`curl -X POST --data "key1=value1&key2=value2" http://example.com` - send POST Data: Sends data as POST request payload  
