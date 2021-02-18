# Practice Lab: Installing Apps in Windows 10

## Summary

In this lab you will learn how install and update Microsoft Store Apps and how to install Microsoft 365 Apps for enterprise from Microsoft 365.

_Dependency Note: To complete this lab, you need to have a Microsoft account. You can use the Microsoft Account that you configured previously in the Module 3 lab: Synchronizing settings between devices lab. You will also use the User2 Microsoft 365 user account, which was created in Module 2 lab: Managing Azure AD Authentication._

## Exercise 1: Installing and updating Windows Store apps

### Scenario

You need to test the download and update functionality of the Microsoft App Store. You will download and install an app named the **Microsoft To Do: Lists, Tasks & Reminders**. You also need to validate how Microsoft Store apps are updated and uninstalled.

### Lab preparation

*Note: In some situations, the Windows Update service may be disabled. Use the following steps to validate and enable the Windows update service if needed. Not that this is not necessary to run in typical Windows 10 scenarios.*

1. Sign in to **SEA-WS1** as **Admin** with the password of **Pa55w.rd**.

2. Right-click **Start**, and then select **Windows PowerShell (Admin)**.

3. In the **User Account Control** dialog box, select **Yes**.

4. In the **Administrator: Windows PowerShell** window, type **the following
    command** and then press **Enter**.

    ```powershell
    Set-Service wuauserv -Startuptype Manual
    ```

5. Sign out of SEA-WS1.

### Task 1: Install a Windows Store app

1. Sign in to **SEA-WS1** with your Microsoft account and the PIN **1029**.

2. In the taskbar, select the **Microsoft Store** icon.

3. In the Microsoft Store app, select **Search**, type **Microsoft To Do**, and then select **Microsoft To Do: Lists, Tasks & Reminders**.

4. Select **Get**.  

   *Note: If prompted by the Your account is missing some key info dialog box, complete the information regarding Birthdate and Country/Region and select **Next**.*

5. If a **Try again later** dialog box appears, select **Close**.

6. Wait for the download and installation to finish and then then select **Launch**.

7. In the message dialog box, select **No** and then close **Microsoft To Do**.

8. Select **Start** and verify that Microsoft To Do is added to the Start menu.

### Task 2: Configure app updates

1. In the **Microsoft Store** app, select the **See more** ellipsis symbol on the menu bar, and then select **Settings**.
2. In **Settings**, under **App updates**, verify that **Update apps automatically** is set is enabled.
3. In the **Microsoft Store** app, select the **See more** icon on the menu bar, and then select **Downloads and updates**. Notice that there are several apps waiting to be updated.
4. Select **Update all**.

5. After the updates start, select **Pause all**.

6. Select **Start**, right-click **Feedback Hub**, and then select **Uninstall**.

7. In the **This app and its related info will be uninstalled** dialog box, select **Uninstall**.

8. Sign out of SEA-WS1.

**Results**: After completing this exercise, you will have installed a Microsoft Store app, managed Microsoft Store app updates, and uninstalled an app.

## Exercise 2: Install Microsoft 365 Apps for Enterprise from Microsoft 365

### Scenario

You have been asked to configure the deployment of the Office 365 apps included in your subscription. You will first assign an Office 365 E5 license to User2 and configure Office installation options. Finally User2 will validate that Office 365 can be downloaded and installed from the Microsoft 365 portal.

### Task 1: Assign a Microsoft 365 license

1. Sign in to **SEA-WS1** with your Microsoft account and the PIN **1029**.
2. In the taskbar, select the **Microsoft Edge** icon.
3. In the address bar, enter <http://portal.office.com>.
4. In the **Sign in** dialog box, enter your admin email address as provided by your instructor. It should be in the form of admin@M365xXXXXXX.onmicrosoft.com and then select **Next**.
5. At the **Enter password** dialog box, enter the password as provided by your instructor. When prompted to save the password, select **Save**.
6. When prompted to **Stay signed in**, select **Yes**.
7. From the App Launcher, select **Admin**.
8. In the Microsoft 365 admin center, in the Navigation menu, expand **Users**, and then select **Active users**.
9. In the User list, select **User2**. This user should have been created earlier in module 2. If you do not have this user, refer to the Module 2 lab: Managing Azure AD Authentication.
10. In the User2 properties, select the **Licenses and apps** tab.
11. In the Licenses list, select **Office 365 E5**, and then select **Save changes**.
12. Close the User2 properties page.

### Task 2: Configure Office installation options

1. In the Microsoft 365 admin center, in the Navigation menu, expand **Settings**, and then select **Org settings**.
2. In the **Org settings** page, on the **Services** page, select **Office installation options**.
3. On the Office installation options page, under Feature updates, select **Once a month (Monthly Enterprise Channel)**.
4. Under Office apps that users can install, remove the check box next to **Skype for Business (Standalone)**, and then select **Save**.
5. Close the Office installation options page.
6. In the top-right corner, select the Account manager button and then select **Sign out**.
7. Close Microsoft Edge.

### Task 3: Install Microsoft 365 Apps for Enterprise

1. On SEA-WS1, in the taskbar, select the **Microsoft Edge** icon.
2. In the address bar, enter <http://portal.office.com>.
3. On the Pick an account prompt, select **Use another account**.
4. In the **Sign in** dialog box, enter User2@M365xXXXXXX.onmicrosoft.com and then select **Next**.
5. At the **Enter password** dialog box, enter **Pa55w.rd1234** and then select **Sign in**. When prompted to save the password, select **Save**.
6. Close all welcome and introduction pages.
7. On the Office 365 page, select **Got it!** close the Office 365 apps prompt.
8. Select **Install Office** and then select **Other install options**.
9. On the My account page, in the navigation pane, select **Apps & devices**. Notice the option to install Office. Also notice that Skype for Business has been turned off.
10. On the Apps & devices page, select **Install Office**.
11. At the bottom of the Edge window, under OfficeSetup.exe, select **Open file**.
12. At the User Account Control, select **Yes**.
13. Office downloads and installs on the local computer. In the notification area, you can select the Office icon to monitor the process as needed. It will take approximately five minutes to complete.
14. After the install completes, select Close to close the Office prompts.
15. On SEA-WS1, select the Start menu and verify that the Office apps display. For example, you should see Word, PowerPoint, and Excel in addition to the other apps included in this subscription.
16. Close Microsoft Edge and sign out of SEA-WS1.

**Results**: After completing this exercise, you will have configured the deployment of the Office 365 apps included in Microsoft 365 and validated an installation of the apps.

**END OF LAB**