Using Office 365 E5 (no teams) with trial
<img width="1823" height="763" alt="image" src="https://github.com/user-attachments/assets/3bda5386-46fc-4652-886d-93d555b895a4" />


# Adding Anti-Phishing Protection Policy

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
<h1>Creating a conditional Policy in Entra ID </h1>

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
<h1>Connecting Microsoft Entra ID logs into Microsoft Sentinel</h1>
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


 
