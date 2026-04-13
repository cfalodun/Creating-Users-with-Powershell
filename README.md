# Active Directory: Bulk User Creation with PowerShell

## Project Summary

This project demonstrates how to create multiple Active Directory user accounts with PowerShell instead of creating them one by one manually in Active Directory Users and Computers (ADUC).

In this lab, Remote Desktop access was first enabled for domain users on the client machine. Then a PowerShell script was run on the domain controller to automatically create multiple user accounts in Active Directory. After that, the new accounts were verified in ADUC and one of the accounts was used to sign in to the client machine to confirm that the setup worked correctly.

---

## Environment & Tools

### Environment
- Microsoft Azure Virtual Machines
- Windows Server (Domain Controller – DC-1)
- Windows 10 (Client-1)

### Technologies Used
- Active Directory
- PowerShell ISE
- Active Directory Users and Computers (ADUC)
- Remote Desktop

### Language Used
- PowerShell

---

## Demonstration

## Step 1: Log in to Client-1 as the Domain Admin

First, log in to **Client-1** using the domain admin account:

```powershell
mydomain.com\jane_admin
```

This account is used because administrative privileges are needed to configure Remote Desktop access.

---

## Step 2: Enable Remote Desktop Access for Domain Users

On **Client-1**, open the Remote Desktop settings and allow domain users to access the machine.

### Steps:
1. Right-click **This PC** and select **Properties**
2. Click **Remote Desktop**
3. Enable Remote Desktop if it is not already enabled
4. Select the option to allow users to connect remotely
5. Add the **Domain Users** group

<img src="https://i.postimg.cc/nr7ZRVtV/09-client1-rdp-domain-users-enabled.png" width="500">

This step allows standard domain user accounts to log in to the client machine, not just administrators.

> In a production environment, this would usually be managed through Group Policy instead of being configured manually on each machine.

---

## Step 3: Log in to DC-1 as the Domain Admin

Next, switch to the domain controller and log in to **DC-1** using:

```powershell
mydomain.com\jane_admin
```

The domain controller is where Active Directory is managed, so this is where the user creation script will be run.

---

## Step 4: Open PowerShell ISE as Administrator

After logging in to **DC-1**:

1. Open the **Start Menu**
2. Search for **PowerShell ISE**
3. Right-click **PowerShell ISE**
4. Select **Run as Administrator**

Running PowerShell ISE as Administrator ensures the script has the permissions needed to create user accounts in Active Directory.

---

## Step 5: Paste and Run the Bulk User Creation Script

In PowerShell ISE:

1. Create a new script file
2. Paste in the bulk user creation script
3. Run the script

<img src="https://i.postimg.cc/NFTYJGwF/10-powershell-bulk-users-created.png" width="500">

The script automatically creates multiple user accounts in Active Directory. This is much faster than manually creating each account through the GUI and is more efficient when onboarding many users.

---

## Step 6: Open Active Directory Users and Computers

After the script finishes running, open **Active Directory Users and Computers (ADUC)** to verify that the accounts were created successfully.

### Steps:
1. Open the **Start Menu**
2. Search for **Active Directory Users and Computers**
3. Open the application
4. Navigate to the **_EMPLOYEES OU**

---

## Step 7: Verify the New User Accounts

Inside **_EMPLOYEES OU**, confirm that the newly created user accounts appear in the list.

<img src="https://i.postimg.cc/Zn3Z7YhJ/11-bulk-users-visible-aduc.png" width="500">

This confirms that the PowerShell script successfully created the accounts in the correct Organizational Unit.

---

## Step 8: Test One of the New User Accounts

To make sure the accounts work correctly, go back to **Client-1** and test login with one of the newly created users.

Use the following credentials:

```powershell
mydomain.com\babega.gej
Password: Password1
```

<img src="https://i.postimg.cc/6qRwj6Nw/12-client1-login-standard-domain-user.png" width="500">

If the login is successful, that confirms:
- The account was created correctly
- The account is active in the domain
- The user can authenticate on a domain-joined machine

This final test verifies that the entire process worked from start to finish.
