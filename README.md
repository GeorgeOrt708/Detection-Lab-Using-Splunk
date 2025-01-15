# How to create a Attack and Defense Cyber Security Lab

## Objective

The primary objective of this cybersecurity attack and defense lab is to create a safe, controlled, and realistic environment for developing, testing, and refining cybersecurity skills such as: reconnaissance, vulnerability analysis, exploitation, privilege escalation, and post-exploitation for Offensive Security and threat detection, log analysis, intrusion prevention, incident response, and system hardening for Defensive Security. This setup enables cybersecurity professionals, students, and enthusiasts to experiment with both offensive and defensive techniques without impacting production systems or violating ethical boundaries.

### Skills Learned

- Setting up and managing virtual machines (VMs) using platforms like VMware, VirtualBox, or Proxmox.
- Designing and configuring network topologies, including VLANs and subnets, for isolation and traffic control.
- Configuring guest operating systems such as Windows Server, Linux distributions (Kali, Parrot OS, RHEL), and specialized security tools.
- Understanding and implementing protocols such as TCP/IP, DHCP, DNS, and routing.
- Using tools like Wireshark to monitor and analyze network traffic.

### Tools Used

- Windows Media Creation Tool
- Virtual Box
- Kali Linux VM ISO's


## Download VirtualBox
  
You will need to download a virtualization software otherwise known as a Hypervisor such as VMware, Hyper-V, or even Virtualbox. For this Lab, we will be using VirtualBox. Download whatever version of Virtualbox fits your current OS using the following link: https://www.virtualbox.org/wiki/Downloads.
![image](https://github.com/user-attachments/assets/971d842a-ff91-4a57-9247-3f396de514c0)

You can customize settings such as where the software will be downloaded to if you have multiple drives, but the defaults work perfectly fine
![image](https://github.com/user-attachments/assets/10f9824d-d31e-4063-bc3a-9b09efa89668)


## Downloading your Virtual Machines.
### For the Windows VM you will need to create a windows OS Image. The safest way to do so will be to create our own via the following link: https://www.microsoft.com/en-ca/software-download/windows10

Once you reach this page you will need to scroll down and click "Create Windows 10 installation media"
![image](https://github.com/user-attachments/assets/6e10f8b2-77fc-4f15-aecb-cf7b1f1a499f)

During the setup process you will be asked to either:

 - Upgrade this PC now
 
 - Create Installation Media (USB flash drive, DVD, or ISO file) for another PC

 Select "Create Installation Media"
 
 ![image](https://github.com/user-attachments/assets/ebc89575-64cc-4272-a91e-25463c822fa2)

You may customize or use the recommended settings for your pc. I recommend using the default settings.

After that you prompted with the option of either:

- USB Flash Drive

- ISO File

  Choose ISO File.
