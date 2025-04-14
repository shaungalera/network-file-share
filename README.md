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
