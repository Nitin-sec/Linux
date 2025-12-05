Tags: [[Commands]]

### **File & Directory Management**
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`cd`|**C**hange **D**irectory → Navigates to a folder 1|Essential for moving into project folders before running build scripts.|
|`cp`|**C**o**p**y file or directory 2|`cp config.yaml config.yaml.bak` → Always backup before editing configs.|
|`less`|View file content page-by-page (allows backward movement) 3|The standard for reading huge log files without crashing the terminal.|
|`more`|View file content page-by-page (forward only) 4|Older alternative to `less`; good to know for legacy systems.|
|`vi`|Text editor (Visual Interface) 5|Quick edits on servers where `nano` or GUI editors aren't available.|
|`cat`|Concatenate/Display file content 6|`cat ~/.ssh/id_rsa.pub` → Quickly copy public keys for access setup.|
|`mkdir`|**M**a**k**e **Dir**ectory 7|Creating structure for new deployments (e.g., `mkdir -p /opt/app/logs`).|
|`rm`|**R**e**m**ove file 8|Deleting temp files. Be careful with `rm -rf` (recursive force).|
|`mv`|**M**o**v**e or Rename file 9|`mv app.jar app.jar.old` → Archiving artifacts during deployment.|
|`pwd`|**P**rint **W**orking **D**irectory 10|Verifying you are in the correct path before running destructive commands.|
|`ls`|**L**i**s**t directory contents 11|`ls -ltr` → Finding the most recently modified files during incident response.|
|`find`|Search for files in a directory hierarchy 12|`find / -name "*.log" -size +100M` → Finding huge files filling up the disk.|
|`grep`|Global Regular Expression Print (Search text) 13|`grep "Error" app.log` → Rapidly finding failures in logs.|
|`tar`|Tape Archive (Group/Compress files) 14|`tar -czf logs.tar.gz /var/log` → Compressing logs for long-term storage.|
|`gzip` / `gunzip`|Compress / Decompress files 15151515|Reducing the size of individual files (like SQL dumps) for transfer.|

### Network commands
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`curl`|Transfer data from/to a server 16|`curl -I http://localhost:80` → Check header response code (200 OK vs 500 Error).|
|`wget`|Network Downloader 17|Downloading install scripts or binaries directly to the server.|
|`ip` / `ifconfig`|Show / Manipulate routing, devices, policy routing 18|Getting the server IP; troubleshooting network interface issues.|
|`netstat`|Network Statistics 19|`netstat -tulpn` → Checking which ports are open and which process owns them.|
|`ssh`|**S**ecure **Sh**ell 20|The secure standard for logging into remote Linux servers.|
|`ftp`|File Transfer Protocol|Legacy file transfer. **SecOps:** Often insecure; prefer `sftp` or `scp`.|
|`ping`|Send ICMP ECHO_REQUEST to network hosts 21|"Is the internet down or just my app?" Basic connectivity check.|
|`telnet`|User interface to the TELNET protocol 22|`telnet google.com 443` → Testing if a specific firewall port is open.|

### Process Management commands
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`ps`|Report a snapshot of current processes 23|`ps aux|
|`kill`|Send a signal to a process (usually to stop it) 24|`kill -9 <PID>` → Forcefully stopping a frozen or zombie process.|

### User management commands
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`id`|Print real and effective user and group IDs 25|Checking if a user belongs to the `docker` or `wheel` (admin) group.|
|`whoami`|Print effective userid 26|Verifying the current user context (e.g., inside a CI/CD pipeline script).|
|`passwd`|Update user's authentication tokens 27|Resetting a user's password or locking an account (`passwd -l`).|
|`su`|Run a command with substitute user and group ID 28|Switching to the `postgres` user to run database commands safely.|

### Application Management Commands
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`which`|Locate a command 29|`which java` → Confirming which Java version/path is being used.|
|`yum`|Package manager (RHEL/CentOS) 30|Installing packages (`yum install nginx`) or applying security updates.|
|`systemctl`|Control the systemd system and service manager 31|`systemctl status docker` → Checking if a service is healthy or failed.|

### Environment Variables Commands
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`env`|Run a program in a modified environment|Listing all environment variables to debug configuration issues.|
|`printenv`|Print all or part of environment 32|Checking if `JAVA_HOME` or API keys are set correctly in the session.|
|`export`|Set an environment variable 33|`export PATH=$PATH:/opt/bin` → Adding custom tools to your path temporarily.|
|`source`|Execute commands from a file in the current shell 34|`source .bashrc` → Reloading configuration files after making changes.|

### Console & Output Management Commands
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`cat`|Concatenate and print to standard output 35|Piping file content into another command: `cat log.txt|
|`clear`|Clear the terminal screen 36|Clearing sensitive output from the screen before a screen share.|
|`echo`|Display a line of text 37|`echo $PATH` → Debugging variables; `echo "hello" > file.txt` → Creating simple files.|

### Some Other Useful Commands
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`systemctl`|Manage Services (Start/Stop/Enable) 38|`systemctl enable nginx` → Ensuring the web server starts automatically after reboot.|
|`df`|Report file system disk space usage 39|`df -h` → Quickly checking if the disk is full (common outage cause).|
|`du`|Estimate file space usage 40|`du -sh /var/log` → Checking size of specific directories to find space hogs.|
|`free`|Display amount of free and used memory 41|`free -h` → Checking RAM usage before launching memory-heavy containers.|
|`chmod`|Change file mode bits (Permissions) 42|`chmod +x script.sh` → Making a script executable.|
|`awk`|Pattern scanning and processing language 43|Extracting specific columns (like PIDs or IPs) from command output.|
|`cut`|Remove sections from each line of files 44|`cut -d: -f1 /etc/passwd` → Listing all usernames on the system.|
|`sed`|Stream editor for filtering and transforming text 45|`sed -i 's/foo/bar/g' config` → Batch replacing configuration values.|
|`ln`|Make links between files (Symbolic/Hard links)|`ln -s /opt/app/v1 /opt/app/current` → Pointing "current" to the active version.|
|`nohup`|Run a command immune to hangups 46|Running a long process that keeps running even if you close the terminal.|
|`crontab`|Maintain crontab files for individual users 47|`crontab -e` → Scheduling backups or cleanup scripts to run nightly.|