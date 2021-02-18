# Practice Lab: Managing Azure AD Authentication

## Summary

In this lab you will create a new user and then join a Windows 10 device to an Azure AD tenant.

### Scenario

You have a new Windows 10 device that you would like to join to your Azure AD tenant. You will create a new Azure AD user account for User2 and then join SEA-WS3 to Azure AD.

*Note: To complete this lab, you need to use the Azure AD tenant information as provide by your instructor. You will also need to use a mobile phone for receiving a text message to finish the Azure AD join procedures as listed in Task 2.*

### Task 1: Create a new user account in Azure AD

1. Sign in to SEA-CL1 as **Contoso\\Administrator** with the password **Pa55w.rd**.
2. On the taskbar, select **Microsoft Edge**.
3. In the address bar, enter <http://portal.azure.com>.
4. In the **Sign in** dialog box, enter your admin email address as provided by your instructor. It should be in the form of admin@M365xXXXXXX.onmicrosoft.com and then select **Next**.
5. At the **Enter password** dialog box, enter the password as provided by your instructor. When prompted to save the password, select **Yes**.
6. When prompted to **Stay signed in**, select **Yes**.
7. If you receive a recommendations prompt, close the window.
8. On the **Welcome to Azure** page, under **Manage Azure Active Directory**, select **View**.
9. In the navigation pane, under **Manage**, select **Users**.
10. On the **All users** page, select **New user**.
11. On the **New user** page, ensure that **Create user** is selected and then enter the following:
     - User name: User2
     - Name: User2
     - Password: Select Let me create the password and then enter **Pa55w.rd**.
12. Select **Create**.
13. Verify that User2 is listed as a member of the Azure AD tenant.

### Task 2: Join a Windows 10 device to an Azure AD tenant

1. Switch to SEA-WS3.
2. Sign in to **SEA-WS3** as **Admin** with the password **Pa55w.rd**.
3. Select **Start**, and then select the **Settings** icon.
4. In **Settings**, select **Accounts**.
5. Select **Access work or school** and then select **Connect**.
6. In the **Set up a work or school account** page, under **Alternate actions** select **Join this device to Azure Active Directory**.
7. On the **Sign in** page, enter User2@M365xXXXXXX.onmicrosoft.com (where the email address represents your tenant reference).
8. On the **Enter password** page, enter **Pa55w.rd** and then select **Sign in**.
9. On the **Update your password** page enter the following and then select **Sign in**:
    - Current password: Pa55w.rd
    - New password: Pa55w.rd1234
    - Confirm password: Pa55w.rd1234
10. On the **Make sure this is your organization** page, verify the tenant name and user name and then select **Join**.
11. On the **You're all set** page, select **Done**.
12. Sign out of SEA-WS3.
13. Sign in to SEA-WS3 as User2@M365xXXXXXX.onmicrosoft.com (where the email address represents your tenant reference) with the password of **Pa55w.rd1234**. A new profile is created for User2.
14. At the **Use Windows Hello with your account** page, select **OK**.
15. At the **More information required** page, select **Next**.
16. On the **Keep your account secure** page, select **I want to set up a different method**.
17. On the **Choose a different method** page, select **Phone** and then select **Confirm**.
18. On the **Keep your account secure** page, enter your mobile phone number and then select **Next**.
19. On the **Phone** page, enter the six digit verification code that is sent to your mobile phone and then select **Next**.
20. On the **Phone verification** page, select **Next**.
21. On the **Success** page, select **Done**.
22. On the **Windows Security** page, in the **New PIN** and **Confirm PIN** boxes, enter **102938** and then select **OK**.
23. On the **All set** page, select **OK**.

### Task 3: Verify the device is joined to Azure AD

1. On **SEA-WS3**, select **Start**, and then select the **Settings** icon.
2. In **Settings**, select **Accounts**.
3. Select **Access work or school** and then notice the **Connected to Contoso's Azure AD** object.
4. Right-click the **Start** button and then select **Computer Management**.
5. Expand **Local Users and Groups** and then select **Groups**.
6. Double-click the **Administrators** group. Notice that **AzureAD\\User2** is listed as a local administrator.
    >Note: The other two SID references refer to the Azure AD global administrator role and the Azure AD device administrator role.
7. Select **Cancel** and then close **Computer Management**.
8. Switch to SEA-CL1.
9. In the Microsoft Azure portal, at the top of the page, select **Contoso**.
10. On the **Contoso** page, under **Manage**, select **Devices**. Notice that SEA-WS3 is listed with a join type of **Azure AD joined**.
11. Close Microsoft Edge and then sign out of SEA-CL1.

### Task 4: Remove the device from Azure AD

1. On **SEA-WS3**, select **Start**, and then select the **Settings** icon.
2. In **Settings**, select **Accounts**.
3. Select **Access work or school** and then notice the **Connected to Contoso's Azure AD** object.
4. Right-click the **Start** button and then select **Computer Management**.
5. Select the the **Connected to Contoso's Azure AD** object and then select **Disconnect**.
6. Select **Yes** to confirm and then in the **Disconnect from the organization** box, select **Disconnect**.
7. On the **Windows Security** page, enter **Admin** with the password of **Pa55w.rd**. Select **OK**.
8. Select **Restart now** to restart SEA-WS3.

**Results**: After completing this exercise you have successfully created a new user and joined a Windows 10 device to an Azure AD tenant.

**END OF LAB**