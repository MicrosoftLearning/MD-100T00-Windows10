# Practice Lab: Managing Local User and Microsoft Account Authentication 

## Summary
In this lab you will configure and manage local accounts and assign a Microsoft account to a Windows 10 device.

### Scenario
You need to create two new local user accounts on SEA-WS1. User1 will be a local administrator and User2 will be a standard user. User1 will also assign a Microsoft account to SEA-WS1 and configure Windows Hello with a PIN.

*Note: To complete Task 2, you need to have a Microsoft account to add to SEA-WS1. You can create a free Microsoft account at https://outlook.live.com. Your instructor can guide you on how to create an account if required.*

### Task 1: Configure and manage local accounts
1.  Sign in to **SEA-WS1** as **Admin** with the password **Pa55w.rd**.
2.  Select **Start**, and then select **Settings**. 
3.  In the **Windows Settings** page, select **Accounts**.
4.  In the Navigation pane, select **Family & other users**.
5.  In the **Other users** section, select **Add someone else to this PC**.
6.  On the **Microsoft account** dialog box, select **I don't have this person's sign-in information**.
7.  On the **Create account** dialog box, select **Add a user without a Microsoft account**.
8.  On the **Create a user for this PC** page, in the **User name** box, enter **User1**.
9.  In the **Enter password** and **Re-enter password** boxes, enter **Pa55w.rd**.
10.  Select three security questions, provide appropriate answers and then select **Next**. The User1 local account is created and listed under **Other users**.
11.  Select **User1** and then select **Change account type**.
12.  In the **Change account type** dialog box, select the drop-down menu and then select **Administrator**.
13.  Select **OK** to return to the **Family & other users** page. Notice that User1 is now listed as an Administrator.
14.  Right-click the **Start** button and select **Computer Management**.
15.  Under **System Tools**, expand **Local Users and Groups**.
16.  Select the **Users** node. Notice that User1 is listed along with other local accounts. Accounts with an arrow pointing downwards are disabled accounts.
17.  Right-click **User1**. Notice the **Set Password** command, used to set a new password for the account.
18.  Select **Properties**.
19.  Select the **Member Of** tab and take note of the default group memberships. Notice that User1 is a member of the **Administrators** group as configured previously.
20.  Select **OK** to close the **User1 Properties**.
21.  Right-click the **Users** node and then select **New User**.
22.  In the **New User** dialog box, enter the following and then select **Create**:
     - User name: User2
     - Password: Pa55w.rd
     - User must change password at next logon: not selected
23.  Select **Close** to close the **New User** dialog box. Notice that User2 is now included in the list of users.
24.  Sign out of SEA-WS1.
25.  Sign in to SEA-WS1 as **User1** with the password of **Pa55w.rd**. Notice that it takes several minutes for the user profile to be created.
26.  At the **Choose privacy settings for your device** page, select **Accept**. The Windows 10 desktop displays.
27.  On the taskbar, select **File Explorer**.
28.  In **File Explorer**, browse to **C:\\Users**. Take note of the user profiles that have been created on this device. 
29.  Double-click **User1** to display the profile content and folders.
30.  Close **File Explorer**.

### Task 2: Configure a Microsoft Account on Windows 10

1.  Verify that you are signed in to SEA-WS1 as **User1** with the password of **Pa55w.rd**.
2.  Select **Start** and then select **Settings**.
3.  In the **Windows Settings** page, select **Accounts**.
4.  On the **Accounts** page, select **Your info**. Notice that User1 is currently signed in as a Local Account.
5.  Select the link that states **Sign in with a Microsoft account instead**.
6.  In the **Microsoft account Sign in** page, enter your Microsoft account email address and then select **Next**.
7.  On the **Enter password** page, enter your Microsoft account password and then select **Sign in**.
8.  If a **Help us protect your account** dialog box appears, select **Skip for now**.
9.  In the **Sign into this computer using your Microsoft account** page, enter **Pa55w.rd** and then select **Next**.
10.  On the **Create a PIN** page, select **Next**.
11.  In the **Set up a PIN** dialog box, enter **1029** in both the **New PIN** and **Confirm PIN** boxes. Select **OK**. Notice that your Microsoft account is now listed on the Your info page.
12.  Sign out of SEA-WS1.
13.  From the Sign-in page, select your Microsoft account and enter **1029** for the PIN. Your account signs in to the desktop.

### Task 3: Remove a Microsoft Account on Windows 10
1.  Verify that you are signed in to SEA-WS1 with your Microsoft account.
2.  Select **Start** and then select **Settings**.
3.  In the **Windows Settings** page, select **Accounts**.
4.  On the **Accounts** page, select **Your info**. Notice that User1 is currently signed in with your Microsoft account.
5.  Select the link that states **Sign in with a local account instead**.
6.  In the **Are you sure you want to switch to a local account** page, select **Next**.
7.  On Windows Security page, enter **1029** for your PIN.
8.  In the Enter your local account info page, configure the following and then select **Next**:
    - User Name: User1
    - New password: Pa55w.rd
    - Confirm password: Pa55w.rd
    - Password hint: default
9.  Select **Sign out and finish**.

**Results**: After completing this exercise you have successfully configured and managed local accounts and assigned a Microsoft account to a Windows 10 device.

**END OF LAB**
