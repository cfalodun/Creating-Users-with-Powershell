# <p align="center">Creating Users With Powershell
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

## Objective

Configure Remote Desktop access for standard domain users and automate user provisioning with PowerShell, then verify accounts in Active Directory and test domain authentication on Client-1.

---

## Step 1 – Enable Remote Desktop for Domain Users

Logged into **Client-1** as:

**mydomain.com\jane_admin**

Steps:
- Opened System Properties
- Selected **Remote Desktop**
- Allowed **Domain Users** access

<img src="https://i.postimg.cc/nr7ZRVtV/09-client1-rdp-domain-users-enabled.png" width="500">

Note: In production environments, this is typically managed using **Group Policy** for centralized control.

---

## Step 2 – Bulk User Creation via PowerShell

Logged into **DC-1** as:

**mydomain.com\jane_admin**

Steps:
- Opened **PowerShell ISE** as Administrator
- Created a new script file
- Pasted the bulk-user creation script
- Executed the script

<img src="https://i.postimg.cc/NFTYJGwF/10-powershell-bulk-users-created.png" width="500">

---

## Step 3 – Verify Users in Active Directory

Opened **Active Directory Users and Computers (ADUC)**.

Verified new user accounts appear under:

**_EMPLOYEES OU**

<img src="https://i.postimg.cc/Zn3Z7YhJ/11-bulk-users-visible-aduc.png" width="500">

---

## Step 4 – Test Domain User Login

Attempted login to **Client-1** using:

**mydomain.com\babega.gej**  
Password: **Password1**

<img src="https://i.postimg.cc/6qRwj6Nw/12-client1-login-standard-domain-user.png" width="500">

---

## Result

- Remote Desktop enabled for Domain Users
- Bulk user creation completed via PowerShell
- Users verified in ADUC under **_EMPLOYEES**
- Standard domain authentication confirmed on Client-1
