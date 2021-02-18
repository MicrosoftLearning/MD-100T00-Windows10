# Practice Lab: Configuring Microsoft Defender Antivirus and Windows Security

## Summary

In this exercise you will learn how to configure Microsoft Defender Antivirus and Windows Security settings.

## Exercise 1: Detecting threats using Microsoft Defender Antivirus

### Scenario

You've been asked to configure and test Microsoft Defender Antivirus on SEA-CL1. You need to configure protection settings to enable controlled folder access and to exclude E:\\Labfiles\\Tools from scanning. You've decided to simulate a virus using a test file, sample.txt, located at C:\Files, to validate successful threat detection.  

### Task 1: Configure Microsoft Defender Antivirus

1.  Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**.
2.  Select **Start**, and then select the **Settings** icon.
3.  In the Settings window, select **Update & Security**, and then select the **Windows Security** tab. Take note of the Protection areas listed under Windows Security.
4.  Select **Open Windows Security**.
5.  In Windows Security, select **Virus & threat protection**.
6.  On the Virus & threat protection page, under Virus & threat protection settings, select **Manage settings**. 
7.  Under Controlled folder access, select **Manage Controlled folder access**.
8.  On the Ransomware protection page, enable **Controlled folder access**. 
9.  Under Controlled folder access, select **Protected folders** to view the default folders that are protected from unauthorized changes.
10.  Click **Back** to return to the Ransomware protection page.
11.  Click **Back** to return to the Virus & threat protection settings page.
12.  Under the Exclusions section, select **Add or remove exclusions**.
13.  On the Exclusions page, select **Add an exclusion** and then from the drop-down list select **Folder**.
14.  In the **Select Folder** dialog box, browse to and select **E:\\Labfiles\\Tools** and then click **Select Folder**. 
15.  Click **Back** to return to the Virus & threat protection settings page.
16.  Click **Back** to return to the Virus & threat protection page.

### Task 2: Perform a scan

1.  On the Virus & threat protection page, select **Scan options**. 
2.  Take note of the options available to configure and then select **Quick scan** and then select **Scan now**.
3.  The quick scan begins and provides information on the number of files scanned and estimated time remaining. The final result should state **No current threats**.
4.  In the Scan options window, select the **Back** button to return to the Virus & threat protection page.
5.  Close the Windows Security window.

### Task 3: Introduce suspicious software

1.  In the Settings window, select the Home button.

2. Select **System** and then select **Notifications & actions**.

3. Under Notifications, enable the **Get notifications from apps and other senders**. This option enables notifications from Microsoft Defender and other apps.

4. Close Settings.

5. On the task bar, select the **File Explorer** icon.

6. In **File Explorer** browse to **C:\\Files**.

7. In the Files folder, double-click **sample.txt**.  

   _**Note**: The sample.txt file contains a text string to test malware detection._

8. In the sample.txt file, **delete both instances of \<remove\>,** including the brackets and any extra lines or blank spaces.

9. Select **Save** and close Notepad.

   _**Note**: Microsoft Defender will immediately detect a potential threat and remove the file. It may take a minute for the file to automatically be removed._

### Task 4: View the quarantined file ###
1.  In the notification area, select the **Notifications** icon, and then in the Action Center, select the notification that states that **Threats found**.
    
 _**Note**: This will open the **Virus & threat protection** page in Windows security. The file is quarantined now._
    
2.  Under Current threats, select **Protection history**. 

3. Take note of and select the **Threat quarantined** item.

4. Read the information about the threat and then select the **Actions** button and then select **Remove**.

5. Close all open windows.

**Results**: After completing this exercise, you will have configured and tested Microsoft Defender Antivirus.

## Exercise 2: Configuring Windows Security Settings

### Scenario

You need to verify that Microsoft Defender SmartScreen has been enabled and is configured on SEA-CL1. You also need to verify that Exploit Protection settings are On by default.

### Task 1: Configure Windows Security

1.  Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**.
2.  Select **Start**, and then select the **Settings** icon.
3.  In the Settings window, select **Update & Security**, and then select the **Windows Security** tab. Take note of the Protection areas listed under Windows Security.
4.  Select **Open Windows Security**.
5.  In Windows Security, select **App & browser control**.
6.  On the App & browser control page, under Reputation-based protection, select **Reputation-based protection settings**. 
7.  Verify that Microsoft Defender SmartScreen has been enabled for apps, files, Microsoft Edge, and Microsoft Store apps. 
8.  Under Potentially unwanted app blocking, select the check box to enable **Block downloads**.
9.  Click **Back** to return to the App & browser control page.
10.  Under Exploit protection, select **Exploit protection settings**.
11.  Verify that System settings are all configured to Use default (On).
12.  Close the Windows Security window.
13.  Sign out of SEA-CL1.

**Results**: After completing this exercise, you will have verified settings related to Microsoft Defender SmartScreen and Exploit protection.

**END OF LAB**