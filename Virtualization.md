Date: 2025-11-30
Tags: [[Linux History & Overview]]

# Virtualization
Virtualization is a technique that allows you to run multiple **operating systems** or **virtual machines (VMs)** on a single physical computer. Instead of each OS needing dedicated hardware, virtualization shares the hardware resources like CPU, memory, and storage.

Think of it like dividing one powerful computer into several smaller ones — each acting independently.

--- 
## Hypervisors
Software that creates and manages virtual machines.
 ### **Types of Hypervisors**
1. **Type 1 Hypervisor (Bare-metal)**
    
    - Runs directly on hardware
        
    - More secure and faster
        
    - Examples: **Hyper-V**, VMware ESXi, Xen
        
2. **Type 2 Hypervisor (Hosted)**
    
    - Runs on top of existing OS
        
    - Easier to set up but slower
        
    - Examples: VirtualBox, VMware Workstation

---
### **What is Hyper-V?**

Hyper-V is Microsoft’s **Type-1 hypervisor** that allows you to:

- Create and run virtual machines on Windows
    
- Test apps, different operating systems
    
- Create isolated environments for security
    

It’s mostly used in servers and enterprise setups, but available on Windows 10/11 Pro as well.

---
### Why virtualization matters

- Saves cost by reducing number of physical machines
    
- Better hardware utilization
    
- Easier testing and development
    
- Helps in cloud computing (AWS, Azure, GCP use virtualization heavily)

# References
What is Virtualization? | Hypervisor Types | Virtual Machines 
# Summary
