<h1>Security Operations Center (SOC) Lab</h1>

<h2>Description</h2>
The project showcases how a basic SOC would be set up using Azure. We set up a Windows 11 Pro VM that has RDP open, this will make it enticing for attackers. We then will set up Microsoft Sentinel so that we can view the security incidents and events that are happening to our VM. 
<br />


<h2>Languages and Utilities Used</h2>

- <b>Microsoft Sentinel</b>

<h2>Environments Used </h2>

- <b>Windows 11 Pro VM</b>
- <b>Microsoft Sentinel</b>
- <b>Microsoft Azure</b>

<h2>Walk-through:</h2>

First, we need to get set up with Microsoft Azure, click "Try Azure for free"
<img src="https://github.com/user-attachments/assets/aba36303-fcb5-47ff-b1bc-9a61da1605bb"/>
<br />
<br />
Click on "Go to Azure portal"
<img src="https://github.com/user-attachments/assets/c4ee66a2-e9b6-42f5-b004-3a11a439026f"/>
<br />
<br />
It will prompt you to make an account or sign in, and complete it as necessary and it will bring you to the dashboard. Click on "Create" on the Virtual Machines button
<img src="https://github.com/user-attachments/assets/d38425ab-f91f-48c2-b2fd-be693c1a3d9c"/>
<br />
<br />
Now click on "Create" then "Azure virtual machine with preset configuration"
<img src="https://github.com/user-attachments/assets/ded8159f-822a-4586-8c81-e86ab6e1dafb"/>
<br />
<br />
We will leave this part as default, click "Continue to create a VM"
<img src="https://github.com/user-attachments/assets/14e5109e-6834-42f2-8a1d-d860a5bc8652"/>
<br />
<br />
Here we will set up our resource group, I named mine "TestGroup", after that we will set our name and region 
<img src="https://github.com/user-attachments/assets/b2e25af8-c1be-4bd3-9ccb-27f92559fb55"/>
<br />
<br />
Scroll down and choose the OS Image, I am using Windows 11 Pro
<img src="https://github.com/user-attachments/assets/4a0fbbb5-3307-4d3c-a29c-3e2bb87517bb"/>
<br />
<br />
Keep scrolling down and set the Username and Password that you will use for the VM. Then make sure that RDP is allowed and click "Next: Disks"
<img src="https://github.com/user-attachments/assets/4fe72ade-92d0-43cf-aafd-272e375bcdd2"/>
<br />
<br />
You can adjust the Disks page but I am just leaving it as default settings. Click "Next"
<img src="https://github.com/user-attachments/assets/1259983c-478c-459f-9c29-2a8455405dc6"/>
<br />
<br />
This page shows the Network settings, the default settings should suffice. Click "Next"
<img src="https://github.com/user-attachments/assets/530f5d96-b877-4044-a524-87df52721f7d"/>
<br />
<br />
Click Next until you get to the "Tags" section and then click "Next: Review + create"
<img src="https://github.com/user-attachments/assets/52edf402-fb0b-4e83-8804-963779b5f283"/>
<br />
<br />
Here it shows the cost, but we are using Azure for free for the time being, click "Create"
<img src="https://github.com/user-attachments/assets/71d158b2-630d-4b42-9820-3c99f40923df"/>
<br />
<br />
Now we can see that the VM is spinning up
<img src="https://github.com/user-attachments/assets/83508e14-ec2f-419c-aaac-a2eef352c1c3"/>
<br />
<br />
Now go to the Sentinel page and click "Create Microsoft Sentinel"
<img src="https://github.com/user-attachments/assets/1bdff03e-36f7-4c0a-b31f-b52e1db90e70"/>
<br />
<br />
Now we have to create a workspace for Sentinel, click "Create a new workspace"
<img src="https://github.com/user-attachments/assets/744c127d-3bb3-42a8-b545-bebbb75c7c2d"/>
<br />
<br />
Make sure that we set the resource group to the same one as the VM, then we will name our workspace and choose our region (make sure the region is the same as the one chosen in the VM creation). Click "Revie + Create"
<img src="https://github.com/user-attachments/assets/714cfc6b-5396-43c4-b895-e0145e6f7394"/>
<br />
<br />
Click "Create"
<img src="https://github.com/user-attachments/assets/6e8203f8-3d41-4fad-bf7b-0ff4a5b850df"/>
<br />
<br />
Now we can add Sentinel to the workspace we just created, click "Add"
<img src="https://github.com/user-attachments/assets/490ea54a-f87a-43a2-8d13-ce30b47e9cf3"/>
<br />
<br />
Now let's go back to our VM to make sure it is all working, we can go to the "Network settings" to see that we have RDP still up and running
<img src="https://github.com/user-attachments/assets/57d90ef1-f872-4cd0-a19b-910cb7370f55"/>
<br />
<br />
Once our Sentinel is up and running we can now go to our dashboard
<img src="https://github.com/user-attachments/assets/657e94a8-f119-43fd-91b2-62d33956627f"/>
<br />
<br />
Now we can go to "Agents" and see that we do not have any Windows computers connected
<img src="https://github.com/user-attachments/assets/17e3a815-137e-49db-89d5-936ba6849603"/>
<br />
<br />
Now we will add our Windows 11 VM, go to "Configuration" and then "Data connectors". Then we will open up the "Content hub"
<img src="https://github.com/user-attachments/assets/939873aa-078d-4d1c-875a-f28d40954779"/>
<br />
<br />
In the search bar, enter "Azure Monitor Agent" and check the box "Windows Security Events" then click "Install"
<img src="https://github.com/user-attachments/assets/924a13fe-74df-40a7-ba1a-4d09a52a8f0e"/>
<br />
<br />
Once that install completes, we can go back to our Sentinel dashboard
<img src="https://github.com/user-attachments/assets/2ac98836-84a1-4743-b178-d28951f3e16e"/>
<br />
<br />
Go back to the "Data connectors" and we can see we have 2 connectors now, we will click "Windows Security Events via AMA" and then click "Open connector page"
<img src="https://github.com/user-attachments/assets/5b65696f-aedd-49f9-b74a-69c789814baf"/>
<br />
<br />
Here we will add a rule name, I named mine "WindowsEventstoSentinel" and made sure my resource group was the TestGroup we made previously, click "Next: Resources"
<img src="https://github.com/user-attachments/assets/ed2da752-c441-4fd5-a6e6-a8543e96d197"/>
<br />
<br />
Here we will add our Windows VM and click "Next: Collect"
<img src="https://github.com/user-attachments/assets/d64d0c43-9ca0-4599-a64b-3132633815e5"/>
<br />
<br />
On this page, I would like to see "All Security Events" and then click "Next: Review + create"
<img src="https://github.com/user-attachments/assets/4d37e6e0-46b1-4bf6-932e-9b178994628e"/>
<br />
<br />
Review the information and click "Create"
<img src="https://github.com/user-attachments/assets/5e591a71-412b-418c-9977-93a901eb2068"/>
<br />
<br />
Now if we go back to the Data connectors page, we can see that we have 1 connected and that we are starting to receive logs
<img src="https://github.com/user-attachments/assets/df517f25-e967-4c08-a671-468382506881"/>
<br />
<br />
Now if we go to our "Logs" page we will see if we are getting any information yet. We can type "SecurityEvent" and click "Run" (we can see that we are not getting any log readings yet)
<img src="https://github.com/user-attachments/assets/d33157f9-391e-435b-acb4-9f4f844568a8"/>
<br />
<br />
Now we will create a new alert rule, click "New alert rule" then "Create Microsoft Sentinel alert"
<img src="https://github.com/user-attachments/assets/f2c134fe-914b-4bea-aa9d-8bf5a24f993b"/>
<br />
<br />
We will create a rule for login attempts because we have RDP open, I will name it "Successful Local Sign Ins" and set the severity to "Medium". Then we can set the MITRE ATT&CK level, we will set this to "Initial Access" and set the status to "Enable". Click "Next: Set rule logic"
<img src="https://github.com/user-attachments/assets/d1a54b40-71e9-439e-8944-a3de33a556c8"/>
<br />
<br />
Now we will create our rule query it will be "SecurityEvent | where Activity contains "success" and Account !contains "system"" (this will show all successful sign-ins that are not system). Then we will set the Query scheduling, I set it to every 5 minutes
<img src="https://github.com/user-attachments/assets/e2007877-7d25-4805-b52a-fa79eaaf8ee1"/>
<br />
<br />
Now if we scroll down, we can set Start running to "Automatically", then we will set the Alert threshold to generate an alert if greater than 0 and "Group all events into a single alert". Click "Next: Incident settings"
<img src="https://github.com/user-attachments/assets/bcdfa297-4f36-48aa-af92-cb2287f95f00"/>
<br />
<br />
Now Enable the Incident settings and click "Next: Automated response" 
<img src="https://github.com/user-attachments/assets/0dff3a8c-b957-4f16-bc1b-2948c4dbc062"/>
<br />
<br />
If you want to use automation here you can but here we will just click "Next: Review + create"
<img src="https://github.com/user-attachments/assets/3d825db9-8383-4573-8a1a-81515e618250"/>
<br />
<br />
Go ahead and review the information and click "Save"
<img src="https://github.com/user-attachments/assets/fdfc9a6d-8568-4713-919a-e0f0467036ef"/>
<br />
<br />
Now we can go to our "Analytics" page and see the active rules, it looks like we are not seeing anything with our new rule
<img src="https://github.com/user-attachments/assets/f3a42cf9-9208-4601-a97c-ebb60fa519e2"/>
<br />
<br />
Now we will RDP into our Windows 11 VM by downloading the RDP file
<img src="https://github.com/user-attachments/assets/45a921a1-9429-415b-b9f3-db12f32a26d0"/>
<br />
<br />
Here we can see that we are signed in to our Windows 11 VM
<img src="https://github.com/user-attachments/assets/5850cda2-affe-4fe1-bfaa-745049c34b67"/>
<br />
<br />
Now we will go back to our Overview page and we can see we have a "Medium" incident
<img src="https://github.com/user-attachments/assets/6a00b74c-040b-4a7c-98c0-7516b2a420b2"/>
<br />
<br />
If we go to the "Incidents" page, we can see that RDP access showed up and our rule is working
<img src="https://github.com/user-attachments/assets/71ff13cb-cc4c-454e-a906-619d5edc40a1"/>
<br />
<br />
We can also go into the incident and see all of the information from the successful logins
<img src="https://github.com/user-attachments/assets/2d54fb91-4559-4b73-a665-4726c37b78bf"/>
<br />
<br />
<h2>I will continue to monitor and update attacks and rules for this SOC in the future!</h2>

