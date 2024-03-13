# SOC-Automation-Project

## Objective

Wazuh instance with soar integration with a fully functional case management using the hive. 

### Skills Learned

- Creating a diagram to show how our lab is built out logically
- 

### Tools Used

- Diagram (draw.io) 
- Virtual Box

### Guides

<a href="https://github.com/GitSavior/Installing-VirtualBox-Instructions/tree/main">Installing VirtualBox Instructions</a><br>
<a href="https://github.com/GitSavior/Creating-Windows-10-VM/tree/main">Creating a Windows 10 VM</a><br>
<a href="https://github.com/GitSavior/Creating-Ubuntu-VM/tree/main">Creating a Ubuntu VM</a>

## Steps

### Step 1: Creating a diagram and how to build out our lab logically. Build a visual to understand of data will flow and the pieces requires that makes it work.

![Network Diagram drawio](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/923cd150-3e02-41f1-92b9-53b616408172)

### Step 2: Install applications and virtual machines. One Windows 10 OS running Sysmon, one Ubuntu Server running Wazuh, and one Ubuntu running Server TheHive.

#### Our newly installed windows 10 OS running sysmon
![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/fcdf1283-24db-4b64-94de-01d4cdcb3612)

#### Our newly installed Ubuntu server running Wazuh
![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/a37b79ef-32eb-4510-824d-15e71cebb41b)

#### Our newly installed Ubuntu server running TheHive
![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/3016a696-eb63-4ea1-afe3-655f66d0b753)

### Step 3: Configure TheHive, Wazuh Server and windows 10 reporting to wazuh

#### Configuring our Windows 10 sysmon to be deployed as a new agent on an Ubuntu server running Wazuh. Selecting the Windows option which will be the type of agent sending the information to the SIEM.

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/ffbbc784-dc05-42b1-88c2-5f2495221f7a)

#### Enter the local IP address of the Ubuntu Server, which will receive information from the Windows 10 machine.

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/834c069a-57bd-4692-9124-ecd79239afa3)

#### Setting the agent name to Project2

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/b2146742-536b-44d9-a18d-268f41977c88)

#### The fallowing command will be entered into Windows 10 PowerShell, which will download software to the Windows system, allowing our agent (Windows 10 machine) to communicate with the SIEM. 

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/ef0d9ac8-36ac-4002-98cf-3bec3c281f17)

#### Finally, entering this command into PowerShell will create a service that will allow the agent to communicate with the SIEM.

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/d63f5a88-de8d-4c56-8a02-d2a6625ad749)

#### After inputting the specified syntax from the steps above into the PowerShell prompt, next the service must be checked to see if it is working, as seen in the image. It is.

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/3796ddbb-d12a-4ee2-88c0-4cb2194e43be)

#### Step 4: Generate telemetry and import it into wazuh. Configure Wazuh and configure Telemetry including Minikatz, which generated Mimikatz custom alert

#### Make a backup before making any changes to the orginial conf

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/bad21e3a-cdd2-4a64-8f60-1e62d361673c)

#### Open Event Viewer. Locate and expand Applications and Services Logs drop down. Locate and expand Microsoft drop down. Locate and expand Windows drop down. Locate and expand Sysmon drop down. right click Operational and select properties. In Gerenal tab copy the Full Name: Microsoft-Windows-Sysmon/Operational.

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/f1000aa0-ab06-4797-95b1-4fa46c782e99)

#### Editing the ossec.conf not the copy. Open Notepad as administrator and then from notepate oopen ossec.conf. Within our syntax add the location copied. For ingest only the Sysmon and active response logs.

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/f48dffae-4bc3-4099-89cc-aa37180a0737)

#### After editing and saving the ossec.conf open services and restart the Wazuh Service

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/617e17eb-6a58-43f4-83ff-29ac2b792b70)

#### In the linux vm with wazuh monitoring the sysmon on the windows machine by filtering only "sysmon"

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/b3bed3e1-eaf9-4011-9490-d09168a85675)

#### In the winwdows machine disable the windows security to be able to download mimikats.

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/590c0640-049d-4e28-92b8-96a7b29d7690)

#### Also, In a web browser like google chrome turn off the safe browsing to be able to download. Go to Settings, Privacy and security, under safe browsing select no protection.

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/a5fe786a-dcfb-488d-b150-b4f08273d6b2)


#### Mimikatz is a toll thatRad Hat hackers use extract credientals from a victim machine. 

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/132aa02e-e339-44e6-982b-8b03c8b3e271)

#### Open powershell, change directory to mimikatz location, run mimikatz

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/7628e3be-dc45-49f4-857f-ce081f23949e)

####


#### Step 5: 
