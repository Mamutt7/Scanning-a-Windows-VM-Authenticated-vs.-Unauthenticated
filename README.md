# Scanning-a-Windows-VM-Authenticated-vs.-Unauthenticated

![image](https://github.com/user-attachments/assets/c0196690-f727-45b9-8f5a-da711492f707)
Inside a VM I created (connection via RDP) I have configured the firewall settings to be set OFF.

![image](https://github.com/user-attachments/assets/ffd00936-0b8d-45f0-ae3c-25353bbb4564)
Here ive created an inbound rule to allow any traffic to flow through the created VM to prepare for vulnerability scanning later.

![image](https://github.com/user-attachments/assets/f18370e8-6e9a-400d-94c1-96914335c842)

Now in within the VM, run this powershell command AS AN ADMIN on your VM to enable remote administrative access by modifying the LocalAccountTokenFilterPolicy registry key. This command sets a registry key that allows local accounts (for example, labuser) to connect remotely with full administrative privileges without requiring elevation:

```
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" -Name "LocalAccountTokenFilterPolicy" -Value 1 -Type DWord -Force
```
