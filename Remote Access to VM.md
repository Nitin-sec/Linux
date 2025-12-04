Date: 2025-11-30
Tags: [[Virtualization]]

# Putty & cmd remote access/ WinSCP
cmd or powershell is better one here

---
### **PuTTY** 
a free and Open-Source terminal, which is widely used for remote access to servers via SSH(Secure Shell). 
**Use when:** VM is Linux-based and you have SSH credentials
**Steps:**
1. Install **PuTTY** on your Windows PC.
    
2. Open PuTTY → In **Host Name** enter:  
    `username@<VM-public-IP>`  
    Example: `ubuntu@52.66.23.100`
    
3. Set **Port** to `22` and Connection type as **SSH**.
    
4. Go to **SSH → Auth → Credentials** (only if using a private key `.ppk`)
    
5. Load your key if needed, then click **Open**
    
6. A terminal will appear → login if asked

---
### **Accessing VM via Windows Command Prompt or PowerShell**

**Use when:** SSH is installed on Windows (usually already available on latest versions)

**Steps:**

1. Open **Command Prompt / PowerShell**
    
2. Run command:
    
    `ssh username@<VM-public-IP>`
    
    Example:
    
    `ssh ubuntu@52.66.23.100`
    
3. If using a private key:
    
    `ssh -i "path/to/privatekey.pem" username@<IP>`
    
4. Accept fingerprint → enter password if required

---
### **WinSCP**
**WinSCP** is a free tool for **securely transferring files** between your Windows PC and remote servers (like Linux servers). It uses secure protocols like **SFTP, SCP, FTP** to move files. It also provides a simple GUI so you can drag-and-drop files just like in Windows Explorer.

### How to Use WinSCP (Quick Steps)

1. **Download & Install**
    
    - Download from the official website (WinSCP).
        
    - Install like a normal Windows program.
        
2. **Open WinSCP**
    
    - You’ll see a login interface.
        
3. **Enter Server Details**
    
    - **File protocol:** SFTP (common for Linux servers)
        
    - **Host name:** Server’s IP address
        
    - **Port number:** Usually 22
        
    - **Username & Password:** Your server credentials
        
4. **Login**
    
    - Accept the server’s key if prompted.
        
5. **Transfer Files**
    
    - Left side = your local computer
        
    - Right side = server files
        
    - Drag and drop files between them.
        
6. **Editing & Managing**
    
    - You can open, move, rename, delete, or set permissions on files directly.

---
# References
Chatgpt

---
# Summary
