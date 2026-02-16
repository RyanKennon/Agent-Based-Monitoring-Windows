<p align="center">
  <img width="560" height="448" alt="image" src="https://github.com/user-attachments/assets/cfbe7c69-7312-4582-aab0-2a4b0d50f768" />
</p>

# Windows Agent-Based Vulnerability Scanning Implementation

This project demonstrates the configuration and execution of an agent-based vulnerability scan within a virtual environment. A scanning agent was deployed and installed on a virtual machine, registered with the vulnerability management platform, and configured with a trigger to initiate scanning. The project highlights how agent-based assessments provide deeper internal visibility compared to external scans and support continuous monitoring of system vulnerabilities.

---

## Environments and Technologies Used

- Microsoft Azure
- Azure Virtual Network
- Tenable (Vulnerability Scanner)

---

## Lab Objectives

- Configure and create an agent-based vulnerability scan  
- Deploy and install a vulnerability scanning agent on a virtual machine  
- Register the agent with the scanning platform  
- Configure a scan trigger for automated assessment  
- Validate agent communication and scan execution

---

## Step-by-Step Walkthrough

### Lab Environment

- **Platform:** Microsoft Azure
- **Client Machine:** Windows 11 Pro

<p align="center">
  <img width="1261" height="349" alt="Capture1" src="https://github.com/user-attachments/assets/fabe3091-9a4e-4ddd-835b-e69219e6fa3c" />
</p>

---

### 1) Create Agent Scan

1. In Tenable **Add Agent Group**
2. Create a **Basic Agent Scan** with these settings:
   - **Basic**
     - **Agent Groups:** Select the recently created agent group
     - **Scan Type:** Triggered Scan
     - **Trigger:** Filename start.tx
    
<p align="center">
  <img width="1313" height="348" alt="Capture2" src="https://github.com/user-attachments/assets/38ca82a2-995a-4f65-9463-e224b4ba7d87" />
</p>

---

### 2) Install Agent on Virtual Machine and Create Trigger

1. Log into **Virtual Machine** and run the following script as an administrator in **PowerShell**
  - **`Invoke-WebRequest -Uri "https://sensor.cloud.tenable.com/install/agent/installer/ms-install-script.ps1" -OutFile "./ms-install-script.ps1"; & "./ms-install-script.ps1" -key "xxx" -type "agent" -name "<agent name>" -groups 'student'; Remove-Item -Path "./ms-install-script.ps1"`**

<p align="center">
  <img width="1112" height="282" alt="Capture3" src="https://github.com/user-attachments/assets/d27f817e-6d93-46f7-b75b-67e903af82a5" />
</p>

2. Once complete navigate to the following folder through **PowerShell**
   - **`C:\ProgramData\Tenable\Nessus Agent\nessus\triggers`**
3. Create a new file called start.txt using the following command:
   - **`New-Item -Name start.txt`**
  
<p align="center">
  <img width="819" height="408" alt="Capture4" src="https://github.com/user-attachments/assets/5b19c2c3-251c-46e4-be6b-1e21fba23c05" />
</p>

4. Navigate to the **triggers folder** and wait for the start.txt document to disappear
5. Check **vulnerability logs** once complete

---

## Outcome

- Successfully created and configured an agent-based scan  
- Installed and registered the scanning agent on the target virtual machine  
- Executed a triggered vulnerability scan through the deployed agent  
- Verified scan results and confirmed agent connectivity  
- Demonstrated continuous and internal vulnerability assessment capabilities

---

## Skills Demonstrated

- Agent-Based Vulnerability Scanning  
- Vulnerability Management  
- Endpoint Security Monitoring  
- Scan Configuration & Automation  
- Virtual Machine Administration  
- Security Assessment  
- Continuous Security Monitoring  
- Remote Agent Deployment  
- Security Operations Workflow
