# SOC-Automation-Project

## Objective

Wazuh instance with soar integration with a fully functional case management using the hive. 

### Skills Learned

- Creating a diagram to show how our lab is built out logically
- Creating a diagram to show the workflow logical process
- Creating VM Servers with Installation of Wazuh and TheHive
- Configuring Thehive Server, Wazuh Server, and Windows to have telemetry
- 

### Tools Used

- Diagram (draw.io) 
- Virtual Box
- Wazuh
- TheHive
- Sysmon
- Mimikatz
- Shuffle

### Guides

<a href="https://github.com/GitSavior/Installing-VirtualBox-Instructions/tree/main">Installing VirtualBox Instructions</a><br>
<a href="https://github.com/GitSavior/Creating-Windows-10-VM/tree/main">Creating a Windows 10 VM</a><br>
<a href="https://github.com/GitSavior/Creating-Ubuntu-VM/tree/main">Creating a Ubuntu VM</a>

## Steps

### Step 1: Creating a diagram and how to build out our lab logically. Build a visual to understand of data will flow and the pieces requires that makes it work. Then build a workflow chart to show the logicial process flow of the lab.

![Network Diagram drawio](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/923cd150-3e02-41f1-92b9-53b616408172)

![2](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/989b3b5b-f76d-4923-b2bc-3f3e14d702d6)

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

### Step 4: Generate telemetry and import it into wazuh. Configure Wazuh and configure Telemetry including Minikatz, which generated Mimikatz custom alert

#### Making Copy of ossec.conf file for good practice. Then opening notpad in administrator otherwise cannot edit the ossec.conf file. Then locating the sysmon in event viewer and copying the full name "Microsoft-Windows-Sysmon/Operational". Then adding that sysmon full name to ossec.conf to use sysmon logs in our Wazuh. Then removing security and system from the log analysis to minimize logging. 

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/4e98dac6-8912-4a1d-a78e-bf5aa73836ec

#### Restarting the Wazuh service after configuring the ossec.conf to allow updated options to be available in our Wazuh.

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/5c5488ef-1410-4f15-8b9e-0942face3117

#### Checking to see if sysmon populates in Wazuh

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/c0a710f6-91ef-46d4-abae-372e4fbdd412

#### Disabling windows security in the downloads file else cannot open minikatz

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/2063df5d-8840-4dfb-8555-e387cd0141d9

#### Disabling Chrome safe browsing else cannot download mimikatz

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/2b5099e9-f16c-41da-9a82-5ccc98e764a0

#### Downloading and running mimikatz

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/67695942-c976-46d3-98e8-bdb980dc0a66

#### Checking to see if mimikatz is pickup by Wazuh

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/59124f12-2f7d-4eec-aec9-c00a01449872

#### Making a backup copy of ossec.conf file. Then editing the ossec.conf file to allow all logs and json logs. Then restarting wazuh to update changes. Then checking to see if the log archives were created. Then editing the filebeats configuration to allow wazuh to be able to ingest the archive logs. Then restarting filebeats to update configuration.

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/506ce7a7-be7e-44c0-a644-8270dfe5d580

#### Creating an index pattern for archive logs to view all the logs regardless is wazuh triggers an alert.

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/47c9251b-9b02-402b-a8b9-87da93a5c100

#### Checking to see if the archives logs and can conclude event are happening in those files. Then grep "mimikatz" with flag -i to ignore case sensitivity to see if an even was picked up. That event was indeed picked up. Then going back to wazuh in discover the in the filter box type mimikats to see the events in more detail.

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/d6ff5e9a-4ee3-4bd1-a798-8f27a1020602

#### Creating a custom rule specificly for mimikatz. Start by copying the 0800-sysmon_id_3.xml and then add it below rule id 100001. Then changing the id 92000 to 100002 in good pratice. Then changing from level 4 to level 15 the highest severity. Changing the field name from "win.eventdata.parentImage" to "win.eventdata.originalFileName" to ensure the file is detected even if the file name is changed. Then changing type to "pre2">(?i)mimikatz\.exe to search speciify for mimikatz. Then removing line 22 to be able to view all the log. Then changing discription name to "Mimikatz Usage Detected." Then changing id to T1003 for credital dumping. Then saving changes and restart wazuh to update new settings.

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/37a21341-92ec-46f3-833d-c67ddfac052e

#### Changing the name of "mimikatz" to "notmimikatz" to verify if our new Wazuh setup will recognize that the mimikatz software executed on the Windows 10 computer is the same file.

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/47a64e94-d772-4a3e-9f24-4239bf4e4bcf

#### Step 5: Connect shuffle our security orchestration, automation, and response (SOAR) platform. Then Send a alert to TheHive and send to SOC analyst via Email.

#### Starting a new workflow. We're adding the webhook app to our process. Copying the URI from the webhook app and pasting it into our ossec.conf file placed on our Wazuh manager. Setting the control find action to "repeat back to me" and calling the execution argument "$exec."

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/21ad3cad-4f29-46d3-94e0-90b8e866e923

#### Configure the wazuh ossec.conf file by adding an integration tag and inserting the webhook URI so that the wazuh manager can connect to Shuffle. Replaced <level> tags with <rule_id> and put "100002" between them to send the rule id to shuffle rather than the level number. <option> was removed because it was not being used. Restart wazuh to allow the changes to take effect, and then verify the status.

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/b1e1ca7d-018a-40a8-a392-33e4e27563f4

#### 3 Starting the webhook and running mimikatz.exe in the windows 10 machine to see the executions within shuffle 

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/5841ebe0-728b-45e8-9d20-bd29844a3e80

#### 4 The hash is concatenated with its hash type, which is a problem. It is critical to extract the hash type added to the hash to allow automation when delivering a hash value to virustotal; otherwise, the value is unreadable because virustotal just looks for the hash value, not the type, while conducting its search. This is accomplished within shuffle by selecting the search action "Regex capture group", then selecting the hashes from the "Input data" after clicking the "+" button, and finally adding a Regex value created by AI to remove the hash type from the beginning of each hash. 

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/392e2576-145b-4a7e-8975-72a7b1275c87

#### Create a virustotal account and copy the unique API key generated for that account. Edit the newly added Virustotal workflow and add the API key, then expand the Hash parameter by clicking the "+" button and selecting the regex output . Save. Rerun the previous execution after adding and configuring the virustotal program to examine what virustotal does and what results it produces.

https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/1dd209f6-12e6-4dd7-a85e-e32ee0bdb6d9

#### The execution result reflects the webpage's output. This file was detected as malicious by 63 out of 72 security vendors.

![image](https://github.com/GitSavior/SOC-Automation-Project/assets/162067776/7e77a56a-5909-4112-b91b-0f867a8fd351)






