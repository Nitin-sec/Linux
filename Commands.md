Tags: [[Commands]]

### **Basic Linux Navigation & System Status**

| **Command**   | **Meaning**                                              | **DevOps/SecOps Use-Case**                                                                           |
| ------------- | -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `pwd` 1       | **P**rint **W**orking **D**irectory → Shows current path | Know exactly where you are before running scripts to avoid deleting the wrong files.                 |
| `whoami` 2    | Displays current logged-in username                      | Validate permissions; ensure you aren't running scripts as `root` unnecessarily.                     |
| `date` 3      | Displays system date & time                              | Critical for correlating logs during incident response (did the attack happen at 2 PM?).             |
| `ls -lt` 4    | List files sorted by **time** (newest first)             | Quickly identify recently modified files (e.g., malware or config changes).                          |
| `ls -a`       | List all files (including hidden ones)                   | **SecOps:** Find hidden config files (start with `.`) often targeted by attackers.                   |
| `clear` 5     | Clears the terminal screen                               | Keeps your workspace clean during long debugging sessions or presentations.                          |
| `history` 6   | Shows list of previously executed commands               | **Forensics:** Check what commands an attacker (or a clumsy colleague) ran recently.                 |
| `man <cmd>` 7 | Displays the **man**ual (help) for a command             | Use during technical screenings if you forget a flag; shows you are self-sufficient.                 |
| `which <cmd>` | Shows the full path of an executable                     | Verify you are running the correct version of a tool (e.g., `/usr/bin/python` vs `/opt/bin/python`). |

---

### **Creating, Viewing & Editing Files**
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`touch <file>` 9|Creates empty file or updates timestamp|**Forensics:** Attackers use this for "Timestomping" to hide file modification times.|
|`cat <file>` 10|Dumps entire file content to output|Quick check of small config files; avoid using on massive log files.|
|`less <file>` 11|Scrollable view; loads file page-by-page|**Interview Favorite:** The correct way to open huge log files without crashing RAM.|
|`head -5 <file>` 12|Displays the first 5 lines of a file|Check CSV headers or the start of a log file to understand the format.|
|`tail -5 <file>` 13|Displays the last 5 lines of a file|Check the most recent errors in a log file.|
|`cp <source> <dest>` 14|Copies a file or directory|**Best Practice:** Always run `cp config config.bak` before editing production files.|
|`mv <source> <dest>` 15|Moves or Renames a file|Renaming files or moving logs to an archive folder.|
|`rm <file>` 16|Removes/Deletes a file|Cleaning up temp files.|
|`rm -rf <dir>` 17|Forcefully removes a directory and contents|**Danger:** Can wipe the server if used on `/`. Use with extreme caution in scripts.|

---
### **Text Processing & Analysis (The "Scripting Power")**
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`grep "text" <file>` 18|Search for specific string in a file|**SecOps:** `grep "Failed password" /var/log/auth.log` to find brute-force attempts.|
|`grep -r "text"`|Recursive search in all files|Finding hardcoded passwords or keys inside a directory of code.|
|`awk` 19|Column-based text processing|Extracting IPs from logs: `awk '{print $1}' access.log`.|
|`sed` 20|Stream Editor (Find & Replace)|Automating config changes: `sed -i 's/8080/80/g' server.conf`.|
|`sort|uniq` 21212121|Sorts lines and removes duplicates|
|`wc -l <file>` 22|**W**ord **C**ount (Lines)|Counting how many requests or errors occurred in a log file.|
|`diff <f1> <f2>` 23|Compares two files line by line|Checking what changed in a config file after a deployment.|

---
### **Permissions & User Management**
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`chmod 777 <file>` 24|Grant Read/Write/Execute to Everyone|**Red Flag:** Never do this in production. It’s a major security vulnerability.|
|`chown user:group` 25|Change file Owner and Group|Ensure the web-server user owns the web files, not `root`.|
|`sudo <cmd>` 26|Execute command as Superuser|**Audit Trail:** Logs _who_ ran the privileged command (unlike `su`).|
|`su <user>` 27|Switch User|logging into a service account (like `postgres`) to run DB maintenance.|
|`id` 28|Print User and Group IDs|Verifying group membership (e.g., is this user in the `docker` group?).|

---
### **Process & Service Management**
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`ps -ef \| grep java` 29|List running processes matching "java"|Verifying if your application backend is actually running.|
|`top` 30|Real-time view of system processes|Troubleshooting high CPU/Memory spikes (finding "zombie" processes).|
|`kill -9 <PID>` 31|Force kill a process by ID|Last resort to stop a frozen application that won't exit gracefully.|
|`pkill <name>` 32|Kill process by name|Faster than finding PID first: `pkill nginx`.|
|`systemctl start <svc>` 33|Start/Stop/Restart services|Managing daemons like `docker`, `nginx`, or `jenkins`.|
|`bg` / `fg` 34343434|Background/Foreground jobs|managing long-running scripts without closing the terminal.|

---
### **Networking & Remote Access**
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`ssh user@host` 35|Secure Shell (Remote Login)|The standard way to access remote Linux servers securely.|
|`scp <file> user@host:` 36|Secure Copy|Transferring config files or logs between local and remote servers.|
|`ping <host>` 37|Check reachability of a host|First step in troubleshooting: "Is the server even up?"|
|`netstat -plunt` 38|Show listening ports/sockets|**SecOps:** Identify unauthorized open ports (backdoors) or conflicting services.|
|`curl <url>` 39|Transfer data from/to a server|Testing APIs or checking if a web endpoint is responding (HTTP 200 OK).|
|`ifconfig` 40|Display network interface config|Finding the server's IP address.|

---
### **System Resources & Storage**
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`df -h` 41|**D**isk **F**ree (Human readable)|Checking if the disk partition is full (common cause of server crashes).|
|`du -sh <dir>` 42|**D**isk **U**sage of a directory|Finding _which_ folder is hogging all the disk space.|
|`free -m` 43|Show free/used memory (MB)|Checking available RAM before deploying a memory-intensive app.|
|`uname -a` 44|Print system/kernel information|Checking kernel version for compatibility or vulnerability patching.|

---
### **Archives & Package Management**
|**Command**|**Meaning**|**DevOps/SecOps Use-Case**|
|---|---|---|
|`tar -czf <name> <dir>` 45|Compress folder into `.tar.gz`|Backing up log directories or application code before deployment.|
|`tar -xzf <file>` 46|Extract `.tar.gz` file|Unpacking software bundles or restoring backups.|
|`zip` / `unzip` 47474747|Zip compression utilities|Working with zip files shared by Windows users/systems.|
|`apt` / `yum` 48|Package Managers (Install/Update)|Automation scripts (Dockerfiles) use this to install dependencies.|

---
