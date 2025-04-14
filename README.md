<p a href="center"

  ![image](https://github.com/user-attachments/assets/7468793b-93eb-4a92-bc50-01f3a1b7e07e)
</p>

<h1>Microsoft Azure Lab: Network File Shares and Permissions</h1>

<h2>Overview</h2>

In this lab, we will work with Network File Shares and Permissions on Microsoft Azure to demonstrate an understanding of file share configurations and permissions. **We will be using the DC-1 and Client-1 virtual machines (VMs) from the previous Active Directory lab.**

<h3>Prerequisites</h3>

1.) Access to the DC-1 VM as a domain administrator account (mydomain.com\jane_admin).<br>
2.) Access to the Client-1 VM as a normal domain user (mydomain\<someuser>).<br>
3.) Previous setup of an Active Directory environment with DC-1 and Client-1.<br>

<h2>Instructions</h2>

<h3>Step 1: Create Sample File Shares with Various Permissions</h3>

1.) **Log into DC-1** using the domain admin account: mydomain.com\jane_admin.<br>
2.) On the C:\ drive of DC-1, create the following four folders:<br />
.read-access<br>
.write-access<br>
.no-access<br>
.accounting<br>

![image](https://github.com/user-attachments/assets/2090b357-f89a-44a4-85e9-9ad42890c79b)

3.) Set the following permissions for each folder:<br />
**Folder**: read-access<br>
**Group**: Domain Users<br>
**Permission**: Read<br>
*(Share the folder with these settings.)*<br />

**Folder**: write-access<br />
**Group**: Domain Users<br>
**Permission**: Read/Write<br>
*(Share the folder with these settings.)*<br />

![image](https://github.com/user-attachments/assets/dcd086d0-92e7-4f74-8b94-9a279d11f261)

**Folder**: no-access<br />
**Group**: Domain Admins<br>
**Permission**: Read/Write<br>
*(Share the folder with these settings.)*<br />

![image](https://github.com/user-attachments/assets/e7fbaae3-709b-4aa6-bef4-7dc9d0b36175)

**Folder**: accounting<br />
*(Do not configure permissions yet; skip this for now.)*

<h3>Step 2: Attempt to Access File Shares as a Normal User</h3>

1.) **Log into Client-1** using a normal user account (mydomain\<someuser>).<br />
2.) Navigate to the shared folders:<br>
.Open file explorer.<br>
.Enter \\dc-1 to access shared folders on DC-1.<br>
3.)Test access to the folders:<br />
.Which folders can you access?<br>
.Which folders can you create files in?<br>

![image](https://github.com/user-attachments/assets/dfab91c7-0de2-4102-ae61-f1b2f7cae957)


<h3>Step 3: Create an "ACCOUNTANTS" Security Group, Assign Permissions, and Test Access</h3>

1.) **Log into DC-1** as the domain admin account (mydomain.com\jane_admin).<br>
2.) Open Active Directory and create a security group named ACCOUNTANTS.<br>
3.) Set permissions for the accounting folder:<br>
**.Folder**: accounting<br>
**.Group**: ACCOUNTANTS<br>
**.Permission**: Read/Write<br>
*(Share the folder with these settings.)*<br>

![image](https://github.com/user-attachments/assets/f754943c-7289-430a-8ca2-928214c60862)
![image](https://github.com/user-attachments/assets/af521147-ad61-43aa-93f0-7129a0219586)


4.) Test access as the normal user:<br />
.On Client-1, while logged in as <buk.fic> (or other user), try to access the accounting share via \\dc-1.<br>
**.Expected Result**: Access to the folder should fail.<br>

5.) Assign <qaki.hof> (or other user) to the ACCOUNTANTS group:<br />
On DC-1, add <buk.fic> (or other user) as a member of the ACCOUNTANTS security group.<br>
Sidenote: You can add entire groups to other groups as well. If we wanted to give access to all of the domain users we would assign 'Domain Users' to the 'ACCOUNTANTS' group instead of buk.fic.<br />

![image](https://github.com/user-attachments/assets/9dbfa7fe-2db7-49d9-89fe-9b40e2bcdd0c)

6.) **Re-test access as** <buk.fic>:<br />
**Log out of Client-1** and log back in as <buk.fic>.<br>
Try to access the accounting share via \\dc-1.<br>
**Expected Result**: Access to the folder should now succeed.<br>

<h2>Conclusion</h2>

By completing this lab, you will have demonstrated:<br />

.Configuring file shares with varying permissions.<br>
.Testing access to file shares from different user accounts.<br>
.Managing Active Directory security groups and applying permissions effectively.<br>
