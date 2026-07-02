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


 
   
   
