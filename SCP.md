Date: 2025-11-30
Tags: [[Remote Access to VM]]

# What is SCP in Linux
`scp` (Secure Copy) is a Linux command used to **transfer files or directories between local and remote systems** (or between two remote systems).  
It uses **SSH encryption**, so data stays secure while copying.
### General Command Structure

`scp [options] source destination`

---
### **Explained Steps**

#### 🟦 1️⃣ Copy a file **from local → remote server**

`scp file.txt user@remote_ip:/path/on/remote/`

**Explanation:**

- `file.txt` → file on your local machine
    
- `user@remote_ip` → username and IP of target server
    
- `/path/on/remote/` → where to store the file
    

You’ll be asked for **SSH password** → file transfers securely.

#### 🟩 2️⃣ Copy a file **from remote → local**

`scp user@remote_ip:/path/file.txt /local/path/`

Same idea, but direction reversed.

#### 🟨 3️⃣ Copy an entire directory

Add `-r` (recursive):

`scp -r myfolder user@remote_ip:/path/on/remote/`

#### 🟥 4️⃣ Copy files **between two remote servers**

`scp user1@server1:/path/file.txt user2@server2:/path/`

---
# References

---
# Summary
