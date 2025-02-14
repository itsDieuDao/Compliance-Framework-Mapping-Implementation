<h1>Compliance Framework Mapping & Implementation</h1>

 

<h2>Objective</h2>
Understand how to map security controls to compliance frameworks (e.g., NIST CSF, ISO 27001, SOC 2) and test compliance in a home lab.
<br/>


<h2>🛠 Step 1: Choose a Compliance Framework</h2>
You can start with NIST Cybersecurity Framework (CSF) since it's widely used and publicly available.<br/>   
  <br/>  
  
🔹 Alternative Options :  
  - <b>ISO 27001 (if you want international standards)</b> 
   - <b>SOC 2 (if you're interested in auditing for service providers)</b>
   - <b>PCI-DSS (for payment security compliance)</b>

👉 For this project, we'll use NIST CSF as our baseline framework. <br/>  
📄 Download the NIST CSF document [HERE](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.04162018.pdf) <br/>  

  
<h2>🛠 Step 2: Set Up Your Home Lab <br/>  
   
🔹 Install a Windows Server & Linux VM </h2>
We'll map compliance requirements to actual security settings in a controlled environment.  
  
 🔧 Tools & Setup:
   - <b>Windows Server 2022 (or 2019) VM</b> - For Group Policy, logging, and access control </b>
   - <b>Ubuntu/Debian VM</b> - For security configuration and compliance scanning </b>
   - <b>pfSense VM (Optional)<b/> - If you want to add firewall policies
 
📌 Install Virtual Machines (VMs)
1. Download and install VMware Worrkstation / VirtualBox
2. Set up Windows Server 2022 and Ubuntu 22.04 VMs
3. Configure a domain controller (Active Directory) on Windows Server <br/>


<h2>🛠 Step 3: Map NIST CSF Controls to Your Lab Environment</h2>
NIST CSF has five core functions:
  
1. Identify 🏷️ – Asset management, risk assessment
2. Protect 🔒 – Access control, endpoint security
3. Detect 👀 – Logging, SIEM, monitoring
4. Respond 🚨 – Incident response plans
5. Recover 🔄 – Backup, disaster recovery
  
🔹 Example Mapping:  
| NIST Function | Control Example | Implementation in Lab |
| ------------- | --------------- | --------------------- |
| Identify      | Asset Inventory | List devices on the network using `nmap` or `PowerShell` `Get-ADComputer` |
| Protect       | Access Control  | Set up Active Directory user roles & GPO for password polices | 
| Detect        | Security Logging | Install **Splunk** or **Wazuh** to collect logs from Windows/Linux |
| Respond       | Incident Response | Simulate a **failed login attack** and analyze logs |
| Recover       | Backup & Restore | Set up **Windows Backup & Linux snapshots** |  

✅ Goal: Implement at least one security control for each NIST function in your home lab.  

<h2>🛠 Step 4: Implement Compliance Controls <br/>  
   
🔹 Install a Windows Server & Linux VM </h2>  
  
  🔧 Tasks:  
  1. Enable Password Policies
      - Open **Group Policy Editor (gpedit.msc)**
      - Navigate to `Computer Configuration > Windows Settings > Security Settings > Account Policies > Password Policy`
      - Set **Minimum Password Length** = **12**
      - Enable **Account Lockout Policy** (3 failed attempts)
  2. **Enable Windows Logging (SIEM Integration)**
      - Open **Local Security Policy (secpol.msc)**
      - Go to `Audit Policy > Audit Logon Events` → Enable **Success & Failure**
      - Install **Splunk** or **Wazuh** to collect logs

  
 <h2>🔹 Linux Hardening (Protect & Detect)<br/>   
  
  🔧 Tasks:  
  1. **Run a Compliance Scan (NIST, CIS Benchmarks)**
     
    bash  
    sudo apt install lynis -y
    sudo lynis audit system  
    
     
<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
