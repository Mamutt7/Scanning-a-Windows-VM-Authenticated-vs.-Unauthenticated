# Scanning-a-Windows-VM-Authenticated-vs.-Unauthenticated

![image](https://github.com/user-attachments/assets/c0196690-f727-45b9-8f5a-da711492f707)
Inside a VM I created (connection via RDP) I have configured the firewall settings to be set OFF.

![image](https://github.com/user-attachments/assets/ffd00936-0b8d-45f0-ae3c-25353bbb4564)
Here I've created an inbound rule to allow any traffic to flow through the created VM to prepare for vulnerability scanning later.

![image](https://github.com/user-attachments/assets/f18370e8-6e9a-400d-94c1-96914335c842)

Now within the VM, run this powershell command AS AN ADMIN on your VM to enable remote administrative access by modifying the LocalAccountTokenFilterPolicy registry key. This command sets a registry key that allows local accounts (for example, labuser) to connect remotely with full administrative privileges without requiring elevation:

```
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" -Name "LocalAccountTokenFilterPolicy" -Value 1 -Type DWord -Force
```
![image](https://github.com/user-attachments/assets/a3ba304d-4db9-43d6-a386-f86a95f0de84)
I've configured settings to run a scan on the VM created during this lab using Tenable and will now wait for the scan results.

![image](https://github.com/user-attachments/assets/67ea2c0c-49f0-4953-a2f3-ebbf80f78648)
The Unauthenticated scan was completed after 10 minutes, and we saw some medium-level severity threats. These will be addressed or remediated in future labs.

An Authenticated scan was done taking 13 minutes to complete, in this scan we saw even more vulnerabilities that were at a higher threat level.
