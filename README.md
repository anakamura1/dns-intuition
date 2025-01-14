<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Building Domain Name System Intuition in Active Directory</h1>
This tutorial will help build general intuition and understanding of how Domain Name Systems (DNS) work in the Active Directory Environment<br />

<h2>Prerequisites</h2>
See the links below to set up for this lab:
Creating Virtual Machines www.github.com/anakamura1/vm-creation
Active Directory Setup

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<p><img width="855" alt="Screenshot 2025-01-10 at 3 06 54 PM" src="https://github.com/user-attachments/assets/b3d5e279-9ae8-4ea7-9c3a-49e9621a0410" />

<p>Log into Client-1 as Jane.Admin and ping "mothership" within PowerShell.</p>
<p>Notice that the request cannot be completed. Type "nslookup mothership" and notice that the DNS cannot resolve this name to an IP address.</p>

<table>
  <tr>
    <td>
<img width="962" alt="Screenshot 2025-01-10 at 3 16 38 PM" src="https://github.com/user-attachments/assets/07461916-ca8e-4828-818f-831be4472cb1" />
    </td>
    <td>
<img width="343" alt="Screenshot 2025-01-10 at 3 16 59 PM" src="https://github.com/user-attachments/assets/ef125d4f-8f50-4b04-9a9a-f655f4850bad" />
    </td>
  </tr>
</table>

<p>Within DC-1 login as Jane.Admin and open up DNS Manager. Navigate to mydomain.com and right click to create a New Host A-Record</p>
<p>Type in "mothership" and have the record resolve it to the domain controller server's IP address.</p>
<p></p>
  <br>

  <p><img width="857" alt="Screenshot 2025-01-10 at 3 17 24 PM" src="https://github.com/user-attachments/assets/6e457ff1-b50a-4e47-aeca-39a4e8b02190" /></p>

<p>In PowerShell if we ping "mothership" we will notice the IP address that it pings.</p>
<br>

<img width="1241" alt="Screenshot 2025-01-10 at 3 18 03 PM" src="https://github.com/user-attachments/assets/d611b6f4-a122-405e-870f-2d4b1ca61e83" />
<p>Back within DNS manager, change the IP address to 8.8.8.8</p>

<br>

<img width="856" alt="Screenshot 2025-01-10 at 3 19 02 PM" src="https://github.com/user-attachments/assets/1fc2d923-64be-4af6-93d5-3eeef83544a7" />
</p>
<p>Ping "mothership" again in PowerShell and notice that it still pings 10.0.0.4</p>
<p>
  This is due to the DNS cache still having mothership as 10.0.0.4
</p>
<br>

<h3>BONUS</h3>

<img width="454" alt="Screenshot 2025-01-10 at 2 56 19 PM" src="https://github.com/user-attachments/assets/e7b28b81-6797-4d5f-8854-3275bb2bc8e2" />

<p>Back in Client-1 as any user, go to Start and search for Event Viewer but open it as an administrator. We can use Jane.Admin here.</p>
<br>
<p><img width="1330" alt="Screenshot 2025-01-10 at 2 58 22 PM" src="https://github.com/user-attachments/assets/5731fe4d-4f93-4d76-ac8e-acf30d68b2de" /></p>

<p>Event Viewer allows us to view security logs. On the left hand side go to Windows Logs -> Security</p>
<p>Right click on Security and click Find. Enter in the user name we were trying to log in as with the wrong password earlier. We can view the failed log in attempts we made.
</p>





