Outlook (mail application) - outlook.office.com
Microsoft 365 admin center - admin.microsoft.com
Microsoft Azure - portal.azure.com
Microsoft Defender XDR portal - security.microsoft.com
It will include your defender for endpoint, defender for office, defender for identity and much more.
Microsoft Intune - https://intune.microsoft.com/#home
Entra ID protection - entra.microsoft.com

1 Module 1
	a. Starting Microsoft 365 E5 (no teams) (trial) and assigning license
	b. Creating a resource group
	c. Creating a windows 11 virtual machine
	d. Creating a Microsoft Sentinel
	e. Generating the telemetry from Microsoft Sentinel Training lab from Content Hub
	f. Installing a Microsoft Sentinel XDR
	g. Creating a detection rule for brute force attack

2. Module 2 : Email Security with Microsoft Defender for Office 365
   A. Creating two users
   B. Adding Anti-Phishing Protection Policy

3. Module 3 : Endpoint Security
   A. Configuring EDR
   B. Onboarding the test vm
   C. Integrating microsoft Intune to the endpoint
   D. Creating Attack Surface reduction rules

4. Module 4: Identity
   A. Creating a conditional Access Policy for Impossible travel
   B. Connecting Microsoft Entra ID logs into Microsoft Sentinel
---------------------------------------------------------------------------------------------------------------------------------------------------------
<h1>a.Starting Microsoft 365 E5 (no teams) and assigning license to it </h1>

Head to the URL 
https://www.microsoft.com/en-us/microsoft-365/enterprise/office-365-e5?activetab=pivot:overviewtab
to start this challenge.
<img width="1823" height="763" alt="image" src="https://github.com/user-attachments/assets/3bda5386-46fc-4652-886d-93d555b895a4" />

After this I select the 1 as the number of person using this and 1 month as length of the subscription.
<img width="1540" height="903" alt="image" src="https://github.com/user-attachments/assets/38e1e679-25aa-4b39-a34c-ebcae822af1c" />

After this enter the username, password and email for setting up.
<img width="706" height="641" alt="image" src="https://github.com/user-attachments/assets/1d02cb08-ad4f-4604-9281-0ca595d6dcbd" />

After this click next and enter the payment method on which first month is free. After everything is done you would be prompted to admin.microsoft.com URL.
<img width="1601" height="748" alt="image" src="https://github.com/user-attachments/assets/8fedd186-1d30-4bae-9efb-0600d09f8e61" />

In this we are trying to install Microsoft 365 E5 (no teams) which we can install it by clicking on the marketplace and search for microsoft 365 E5.
<img width="1750" height="837" alt="image" src="https://github.com/user-attachments/assets/f1efa60a-e22f-46df-8df3-b32d42464aea" />

Click on Details and select Microsoft 365 E5 (no teams) (trial) as the plan and start the trial.
<img width="1900" height="747" alt="image" src="https://github.com/user-attachments/assets/0870118c-6eba-4520-9aef-18cccdbc0ee4" />

After this we can see Microsoft 365 E5 (no teams) which we just installed in the Product section.
<img width="1428" height="481" alt="image" src="https://github.com/user-attachments/assets/5cbe0d83-1712-4c0e-91e9-a7581ffcff2d" />

Since we havenot assigned any licenses to it, head over to the Users > Click on your User > Licenses and apps > check on Microsoft 365 E5 (no teams) is checked on.
<img width="638" height="684" alt="image" src="https://github.com/user-attachments/assets/3e7568a1-ebf5-4667-ac3a-6baa7622cb78" />


The next thing we want to do it since Microsoft 365 E5 is up and running, we want to create a microsoft azure portal account. To do that head over to portal.azure.com website.

Note: If you havenot used Azure before you should be able to start the azure with free trial.
<img width="1547" height="589" alt="image" src="https://github.com/user-attachments/assets/90374424-9b2e-4721-8fde-5bf9d74c0164" />

Just click on it and follow the instructions.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1>b. Creating a Resource group</h1>
- For creating a resource group, just go into portal.azure.com
- Search for Resource group
- Click on create
<img width="2693" height="532" alt="image" src="https://github.com/user-attachments/assets/c6da1f06-0d44-4bb2-bf38-bfc9ce7260e2" />

Now any resource you create going forward, such as virtual machines, should be stored under this newly created resource group to stay organized.

Note: Make sure you have the location set it to East US.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1>c. Creating a windows 11 virtual machine</h1>

For this search virtual machine under portal.azure.com and click on Create > virtual machine.
<img width="1281" height="938" alt="image" src="https://github.com/user-attachments/assets/8c6745ec-4534-4a44-a3c3-3d73136a6340" />

- Enter the details for resource group which we just created. Enter the name of the virtual machine, Region, Availability options set it to no infrastructure redundancy required, Image set it to windows 11, size set it to B series, enter    the username and password and click on Disks.
<img width="865" height="629" alt="image" src="https://github.com/user-attachments/assets/58591ee3-afee-4476-91ac-e210d8c6fb4b" />

- Under networking Check Delete public IP and NIC when VM is deleted.
<img width="961" height="389" alt="image" src="https://github.com/user-attachments/assets/8d95e56e-dfcc-4153-b051-adc5d23b1a3e" />
- Then click on Review and Create.
- After the deployment is done, Click on the vm which you just created.
<img width="2526" height="1144" alt="image" src="https://github.com/user-attachments/assets/af9600f7-9be2-4e68-832c-afbce0b06667" />
Here devraj-vm is the name of the windows 11 virtual machine which i have created

 Note: While creating our virtual machine we saw RDP 3389 can be used to access the virtual machine from any ip address. So we can change the firewall rule to set it from our IP Address only for this lab.
 - Click on Networking > Network settings and set Source from only our IP Address.
<img width="2189" height="719" alt="image" src="https://github.com/user-attachments/assets/aa0a0293-93f9-4945-b5fd-dfb85d813a40" />

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<h1>d. Creating a Microsoft Sentinel</h1>

What is Microsoft Sentinel? 

Security teams today face a growing challenge: too many alerts, limited visibility, and increasing pressure to respond quickly. Microsoft Sentinel was built to address these exact problems.

Microsoft Sentinel is a cloud-native platform that combines SIEM (Security Information and Event Management) with SOAR (Security Orchestration, Automation, and Response). It helps security teams detect threats, investigate incidents, and automate their response all from a single interface in the Microsoft cloud.

Why Use Microsoft Sentinel

Sentinel is designed for modern security operations centers that need to scale, move faster, and make decisions based on real insights. It provides:
- A unified view across your users, devices, applications, and infrastructure
- Built-in analytics and threat intelligence to surface real threats
- Automation tools to reduce manual work and speed up incident response
- Full visibility across both Microsoft and non-Microsoft environments

You do not need a Microsoft Defender XDR or E5 license to start using it.

<b>Core Capabilities of Microsoft Sentinel</b>

Prebuilt Security Content

Sentinel includes ready-to-use detection rules, workbooks, and templates that help you get started without writing everything from scratch. You can immediately begin ingesting logs, setting up alerts, and building dashboards tailored to your environment.

Scalable Data Collection

Sentinel connects to a wide range of data sources. You can pull in logs from Microsoft Entra ID, Defender for Endpoint, Azure resources, Microsoft 365, and third-party platforms. It also supports integration through Syslog, the Common Event Format, and custom APIs. All collected data is normalized for consistent analysis.

Threat Detection

Sentinel helps reduce noise by grouping related alerts into incidents using built-in analytics. These detection rules are mapped to the MITRE ATT&CK framework and can be customized to fit your environment. You can also enrich detections by integrating threat intelligence feeds and applying watchlists for high-value assets, former employees, or service accounts.

Investigation and Hunting

Once alerts are triggered, Sentinel provides tools to investigate and uncover the root cause. You can use the visual investigation graph to explore relationships between users, IPs, and devices. You can also run threat hunting queries using Kusto Query Language, or extend your investigations using Jupyter notebooks for advanced analytics and custom visualizations.

Automated Response

Sentinel supports automation using playbooks built with Azure Logic Apps. These playbooks can take actions such as creating tickets, sending notifications, or blocking users. You can trigger them manually or automatically based on the alert or incident. Sentinel offers connectors for popular tools like ServiceNow, Jira, Microsoft Teams, and more, so you can build custom workflows that fit your environment.

Designed for the Needs of Modern Security Teams

Sentinel is built for security teams that need to do more with less. It provides the visibility, intelligence, and automation required to defend against modern threats. Since it runs entirely in the cloud, there is no infrastructure to maintain, and you can scale as your organization grows.

- Search for log Analytics workspaces under portal.azure.com. Click on Create. Enter the resource group name and name of the instance for log analytics and click Review + create
   <img width="2876" height="472" alt="image" src="https://github.com/user-attachments/assets/8395cafa-0cd0-4985-acce-b6ef09e34335" />

- Search for Microsoft Sentinel under portal.azure.com and click Create. It will tell you to add Microsoft sentinel to your workspace which we have just created. Just select it
<img width="3408" height="1136" alt="image" src="https://github.com/user-attachments/assets/bfd2d955-b3c8-41c5-b140-b9de23430b4a" />

- This is basically your SIEM where you can write your KQL queries to search for malicious activity.
- Microsoft Sentinel uses KQL language for querying.
- It allows security teams to
=> Ingest and centralize logs from Microsoft Defender, Entra ID, office 365.
=>  we can also ingest third party data sources like Cisco and Fortinet firewalls.
=> Create Custom Detections for suspicious behavior, correlate signals from endpoints, identities, Cloud Apps
=> Run automated workflows using playbooks.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<h1>e. Generating the telemetry from Microsoft Sentinel Training lab from Content Hub</h1>
- Go to portal.azure.com
- First thing we can do is CLick on Subscriptions > Your Subscription > Activity log > Export Activity Logs > Add diagonistic setting
- It will tell us what kinds of logs do we want to send.
- Here I will select Administrative, Security and Alert under Categories and under Destination details I will check on Send to Log Analytics workspace which we have created before.

<img width="1294" height="743" alt="image" src="https://github.com/user-attachments/assets/db6511f7-822a-4351-9ce9-278386534d55" />


To connect our Azure Actiivity to Microsoft Sentinel we can head it to Content hub under Microsoft Sentinel. Select Azure Activity and install it.
<img width="2819" height="1045" alt="image" src="https://github.com/user-attachments/assets/76605446-2c1c-4761-ac87-8f00eb74c327" />

Similarly, we are going to install Microsoft Sentinel training lab. In previous versions we can just search in Content Hub. But recently Microsoft have removed this feature. For this few additional steps are required.
=> Open the powershell which we can open by clicking as shown in the figure below.Entered the command: az identity create --resource-group <your-resource-group> --name SentinelDetectionRulesIdentity where <your-resource-group> is the resource group that you have created.
<img width="655" height="282" alt="image" src="https://github.com/user-attachments/assets/3f23455b-ae99-46f3-b4f3-6d30266a6774" />

=> Click into the link below https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FAzure-Sentinel%2Fmaster%2FTools%2FMicrosoft-Sentinel-Training-Lab%2FPackage%2FmainTemplate.json which will open creating custom deployment. Finally deploy into Azure as shown in the figure below.
<img width="860" height="859" alt="image" src="https://github.com/user-attachments/assets/5ebeba92-3959-4b57-8b90-bffcf36f9564" />

Important URL
UAMI: https://github.com/Azure/Azure-Sentinel/blob/master/Tools/Microsoft-Sentinel-Training-Lab/README.md

Onboarding: https://github.com/Azure/Azure-Sentinel/blob/master/Tools/Microsoft-Sentinel-Training-Lab/Exercises/Onboarding.md

- Go to Logs under Microsoft Sentinel and click on tables where you can find the name of the table and start playing on them.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1>f. Installing a Microsoft Sentinel XDR </h1>

- For this head into portal.azure.com and select Microsoft Sentinel > Content Management > Content Hub and search for Microsoft Defender XDR. and install it.
<img width="2684" height="1093" alt="image" src="https://github.com/user-attachments/assets/8fb225ea-86f3-420a-a7ee-2d4fde80e60a" />

- Then under Data connectors select Microsoft Defender XDR and under connect events section i will just select both of them Microsoft Defender Alerts (AlertInfor, AlertEvidence). What this means is it will now begin ingesting alerts from Microsoft Defender XDR, including those from endpoints, email and identity platforms. For this we actually need to enable this connection from Microsoft XDR as well. 

<img width="1843" height="803" alt="image" src="https://github.com/user-attachments/assets/d434058e-de89-4795-8ce0-e882e7a8f337" />

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<h1>g. Creating a detection rule for brute force attack</h1>

 - For this just go to Microsoft Sentinel > Analytics > Create > Scheduled query rule
<img width="885" height="701" alt="image" src="https://github.com/user-attachments/assets/85653f0d-dfbc-42db-9d39-ca734587c29b" />

<img width="713" height="926" alt="image" src="https://github.com/user-attachments/assets/40937482-9e31-4de0-8b73-f9fe4738e81d" />

Then under Incident settings set it to enabled. Click on next and save.

<img width="2025" height="825" alt="image" src="https://github.com/user-attachments/assets/84b6495e-3731-45d4-836d-f43a592fbcc2" />

This rule will now trigger an alert if an account has more than 1000 failed logon attempts. 

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<h1>Module 2 : Email Security with Microsoft Defender for Office 365</h1>
It will allow us to simulate, detect and investigate phishing threats.  

<h1>A. Creating two users</h1>

- For this heading over to admin.microsoft.com and signing it with my credentials.
- Click on add user which is on top of the page.
<img width="1763" height="645" alt="image" src="https://github.com/user-attachments/assets/f9ebecd0-44f4-426c-bede-44698cea8d32" />
- Here I am going to create two users Bob Smith and Jenny Smith
<img width="1747" height="1097" alt="image" src="https://github.com/user-attachments/assets/6526f6a0-1b6d-4dad-ae06-06117d226fd6" />
- Now we need to log into their outlook (mail application) in order to activate their mailboxes.
- To do that we can just simply type in outlook.office.com and login with the email and password which we just created above.
-  Then we go to URL security.microsoft.com (Microsoft Defender XDR) and select Email and collaboration on the left hand side.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1>B. Adding Anti-Phishing Protection Policy</h1>

This uses machine learning and user defined rules to detect the following
- Emails that are pretending to come from trusted domains or users
- Spoofed display names or reply-to-addresses
- Lookalike domains (micros0ft.com vs microsoft.com)

If impersonation attempt is detected, the email is either quarantined or redirected based on your policy.

To set it up I followed the following procedures:
1. First heading into microsoft defender portal by heading into security.microsoft.com. Then clicking into Email & collaboration and select Policies & rules.
<img width="1890" height="849" alt="image" src="https://github.com/user-attachments/assets/98f18acc-fdf4-421f-bbbf-8d8e215eac78" />

2. Then click into Anti-phishing. however there is already a default policy that is created by Microsoft. But we will create it our own. Just click on create.
<img width="1312" height="446" alt="image" src="https://github.com/user-attachments/assets/5af5b13e-63fc-468a-bc2e-29ffa2e1084b" />

3. Then click on next.
4. After this comes the user, groups, and domains. FOr this i will be selecting Domains which we did same as in Creating Safe link Policy.
<img width="1856" height="586" alt="image" src="https://github.com/user-attachments/assets/14933e59-fc61-422d-9631-3f680e816ff6" />

5.  Click on Next. Then comes the important one Phishing threshold & protection.
   -  Phishing email threshold - Message are identified as phishing with a low, medium or high degree of confidence.
   -  Enable users to protect - Here usually the people like CEO, CFO, executives, very important people are added. Apart from this finance team people are added here.
   -  Enable domains to protect - Add the domains that we own in the company. It can also be a custom domain (sub-branch, third-party) 
   -  Add trusted senders and domains- What this does is that it learns typical senders and communication patterns for a user. So that it can flag unusual or impersonated messages.And they do this via AI.
   -  Enable spoof intelligence - which is also enabled by default and very much recommended.
   -  Then click on Next.
<img width="1813" height="1200" alt="image" src="https://github.com/user-attachments/assets/96b40d7b-4925-4ea2-a949-f2ac3cde872b" />

6. Then comes with the Action.and press submit
<img width="1879" height="1206" alt="image" src="https://github.com/user-attachments/assets/e3425739-0a37-4353-93c9-1e363632ad3d" />
<img width="1668" height="426" alt="image" src="https://github.com/user-attachments/assets/b464fea4-9c94-4b9f-91e9-f381b54886da" />

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1>Module 3 : Endpoint Security</h1>
=> Onboarding our test virtual machine with Microsoft Defender for endpoint so that we can start sending real endpoint telemetry. Once you are connected you will be able to detect malicious files, suspicious commands, lateral movement and many more.
=> Microsoft Defender is your Enterprise grade EDR your endpoint detection and response platform. It continuously monitors your endpoint like your test vm, for things like process executions, file creations, registry changes, network connections. 

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
A. Configuring EDR
- Go to System > Settings > Endpoints > General > Optional Features
- Make sure it is set to on for Enable EDR in block mode.
- Custom network indicators is also set to ON.
- Turn ON web content filtering
- Turn ON Live response
- Turn ON microsoft Intune connection

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
B. Onboarding the test vm 
	-  Go to System > Settings > Endpoints > Device Management > Onboarding
	- Select Operating System
	- Then follow the option from there
   - Click on Download onboarding package and paste into the device which you want to onboard.
   - After logging into the device, run this file as administrator. Just run this file and 
   
   - Then we are going to run the detection test which is shown in the instructions above in the microsoft defender.
   - Just paste that command into the device and after some time you can see your device as onboarded. 
	

   <img width="1522" height="734" alt="image" src="https://github.com/user-attachments/assets/ea82918f-1e6f-453b-8fac-9bf0ca2a9f4d" />

   <img width="1522" height="734" alt="image" src="https://github.com/user-attachments/assets/364abf30-f0f7-404e-98be-ffe71a6458c4" />

   <img width="1114" height="430" alt="image" src="https://github.com/user-attachments/assets/b8383198-119a-4036-b73a-65c62de6804b" />

   <img width="1619" height="1156" alt="image" src="https://github.com/user-attachments/assets/fc11ab07-c502-470b-b62e-0588bcb3a771" />

- After you have successfully onboarded the device you can see your device in Assets
  <img width="3323" height="734" alt="image" src="https://github.com/user-attachments/assets/f67ca99a-d142-4d70-8ffd-f00bfdcf8492" />
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1> C. Integrating Microsoft Intune to Microsoft Defender </h1>
  Microsoft Intune is the enterprise platform which is used to manage and protect endpoints at scale. Here we are trying to configure attack surface reductions (ASR rules) which are a set of protections that help block real world malware techniques like
  		- office macros spawning PowerShell
		- credential theft via LSASS
		- ransomware encryption behavior
		- Files downloaded from the internet 
These rules are used by real organizations to harden their endpoints

- First heading to Microsoft Intune admin centre (intune.microsoft.com)
- For this first we have to enroll the device which we can do it by going to Device onboarding > Enrollment > Automatic Enrollment
  
<img width="1005" height="926" alt="image" src="https://github.com/user-attachments/assets/ff5ac230-c514-441f-a9f9-50d7f194bae5" />

- Click on Save

- Then RDP into your VM and search for access work or school. click into it and again click into Join this device to Microsoft ENTRA ID.
<img width="900" height="371" alt="image" src="https://github.com/user-attachments/assets/3cdf9fa3-1d10-4b7c-9320-a85bca706580" />

<img width="627" height="501" alt="image" src="https://github.com/user-attachments/assets/3e8c1f0c-21c7-4a52-a9a4-f0abe49305c0" />

- Then login with one of the user that you have created. Once you have successfully logged in, you would be shown like following:
<img width="679" height="282" alt="image" src="https://github.com/user-attachments/assets/4e49e56a-e471-401c-8dd2-21580ce768f6" />

- Click on Join and you are all set.

- Then again RDP into the machine using credentials which you just used. Search RDP > Advanced > User Authentication > click into it.  Make sure that after we have checked this option we cannot login from the IP Address. So we have to enter our device name which we can find under our Virtual Machines > Device Information.
- Sometimes you might get an error saying the devices are not in the same network. So for this open notepad (using administrator) > Open > C:/windows/System 32/ drivers/etc/hosts
- 127.88.21.22 devraj-vm in this format
 <img width="1003" height="652" alt="image" src="https://github.com/user-attachments/assets/00185e78-8ea2-46af-853f-16b2ee604e70" />

- After this when we try to RDP into the machine again we should get a pop up allowing us to login with the test account. Enter the login credentials.
	-  Then in Devices>Overview we can see our device gets onboarded.
<img width="1942" height="926" alt="image" src="https://github.com/user-attachments/assets/8f23bcb5-fc44-4000-afd0-9533f28232c1" />

After this we are going to make some changes to the settings of Microsoft Defender for endpoint under Setup.
	- Go to Endpoint Security >Setup > Microsoft Defender for Endpoint >
	- Put it on for following
		- Allow Microsoft Defender for endpoint to enforce endpoint security configurations
		- connect windows device versions 10.0.01.5603 and above to Microsoft defender for endpoint
		- click on save
		- Now we can put on policies to enforce 

<img width="1139" height="807" alt="image" src="https://github.com/user-attachments/assets/10ba7d22-1171-48be-b66f-17c6b5850d84" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1>D. Creating Attack Surface reduction rules</h1>
Now that our endpoint is enrolled into intune. 
	- Go to Endpoint Security > Manage > Attack Surface Reduction > Create Policy
		- Select the platform and profile (Attack Surface Reduction rules)
		- Under configuration Settings 
				- block all office applications from creating child processes
				- Block credential stealing from the windows local security authority subsystem
				- Use advanced protection against ransomware
				- Block process creations originating from PSExec and WMI commands
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------		
<h1>Module 4: Identity Protection</h1>

Identity is one of the first things the attacker go to. We need to know how Entra ID helps detect it. For this we are using **Entra ID protection** which continuously monitors users sign in and monitors account behavior.
it will looks for anomalies such as
		- Impossible Travel
		- Sign-ins from unfamiliar locations
		- Password spray and brute force
		- Token replay and session hijacking
		- Users flagged as high-risk
	- For this we go into **entra.microsoft.com**
	- **User risk** means long term account risk
	- **Sign in risk** is a risk that is tied to a specific login
	- Conditional access is the if something is risky then do something.  
	- Under Report we can see 
		- Risky Users means these are the accounts that were flagged for suspicious behavior
		- Risky sign-ins means these are the accounts with the red flags. For example sign ins from anonymous IP, impossible travel, unfamiliar signs and many more.

<img width="2940" height="1258" alt="image" src="https://github.com/user-attachments/assets/2aececcf-89bd-4284-9ea2-978824152536" />

- This is where Identity management and protection happens in Microsoft 365.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1>A. Creating a conditional Access Policy for Impossible travel </h1>

If the signin looks risky then force Multi-factor authentication. or if this user is logging in from the country we dont trust then block access entirely. 
Here we are trying to create a conditional access policy for Impossible travel
For this go to entra.microsoft.com. Click on ID Protection > Dashboard > Conditional Access > Named Locations > Countries Location.
<img width="1902" height="669" alt="image" src="https://github.com/user-attachments/assets/8b88ac48-3a0d-4548-98ab-4eea88338852" />

Click on Countries Location
<img width="729" height="1197" alt="image" src="https://github.com/user-attachments/assets/8f58686f-ecae-4404-ba6e-92e396f045be" />

Suppose in our company all of them are in Canada and there is no employee working from other countries. Fill out the details. Click on Create.

Note: Also make sure that Security Defaults is disabled before enabling your own policy. After disabling click on Save.
<img width="521" height="1199" alt="image" src="https://github.com/user-attachments/assets/6800e226-cfa0-4564-b66f-c7d295b1476d" />

After this Click on Conditional Access > New Policy.Then enter the policy name. I have written as MYDFIR-devraj-CAPolicy.
Under Users select the users you want to include. For condition
<img width="1078" height="1213" alt="image" src="https://github.com/user-attachments/assets/8d8f7a90-1617-40fd-9b7e-a3a547f3d11a" />

For condition you can include the Blocked countries policy which you just have created.
<img width="3084" height="1037" alt="image" src="https://github.com/user-attachments/assets/dd3c64f0-3008-418b-8114-7c5fce038c93" />

Now For example an employee of our company will try to access outlook from countries except canada, then this will show on during login.
<img width="541" height="446" alt="image" src="https://github.com/user-attachments/assets/6d735098-0adc-4759-803f-9e138329048e" />


 ------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1>B. Connecting Microsoft Entra ID logs into Microsoft Sentinel</h1>
To begin start heading into portal.azure.com
Head into Microsoft Sentinel which you have created and go to Content Hub. For me at this time it is saying this portal has been moved to Microsoft Defender XDR. Just click into it and search for Entra ID and install it.
<img width="3376" height="1270" alt="2026-07-09 17_14_29-Content hub - Microsoft Defender" src="https://github.com/user-attachments/assets/d9e3eada-a628-4515-8f58-817f7721a186" />

After this click on Microsoft Sentinel > Configuration > Data connectors.
Select Microsoft Entra and Open connectors page.
<img width="3387" height="1246" alt="image" src="https://github.com/user-attachments/assets/1bd7649d-73c6-447e-94fe-3ae42b74ca25" />

After this, Select Sign-in Logs and Audit Logs and click on Apply changes.
<img width="1021" height="735" alt="image" src="https://github.com/user-attachments/assets/a0e07b98-2ff8-4732-affb-5e1450fe1313" />

Now we want to generate some kind of activity so i head towards my outlook account and login. 

After this I login with the bob account which we have created before to generate some telemetry.


 
