# Practice Lab: Managing Windows 10 Settings


## Summary

In this lab you will learn how to configure computer settings using Windows Settings, the Control Panel, and Windows PowerShell. You also learn how to customize and deploy a custom Windows 10 Start page layout.

## Exercise 1: Configuring Settings Using Windows Settings and Control Panel

### Scenario

You need to use Windows Settings to validate protection settings, device specifications, and Windows specifications. You also need to determine which applications are slowing down the startup process for Windows 10. Finally, you need to create a new power plan that minimizes power usage, but does not impact multimedia presentations while the device is running on battery.

### Task 1: Using Windows Settings

1.  Sign in to SEA-CL1 as **Contoso\\Administrator** with the password **Pa55w.rd**.
2.  Select **Start,** and then select the **Settings** icon. 
3.  In **Windows Settings**, select **System**, and then select **About**. Take note of the protection settings, Device specifications, and Windows specifications.
4.  Select **Storage**. Take note of the storage information including how storage is used on the device.
5.  Select **Multitasking**. In the Multitasking page, under **Timeline** disable the **Show suggestions in your timeline** option.
6.  Select **Home**.
7.  In **Windows Settings**, select **Apps**, and then select **Apps & features**. Take note of the Apps & features installed on the device.
8.  Select **Startup**. Take note of the apps that are configured to start when you sign in to the device. Notice that Microsoft OneDrive has a high impact to the startup of the device.
9.  In the **Startup** page, disable the **Microsoft OneDrive** option. This will prevent OneDrive from starting automatically.
10.  Select **Home**.
11.  Close **Windows Settings**. 

### Task 2: Using Control Panel

1.  Select **Start** and type **Control Panel**. Press **Enter**.
2.  In the Control Panel window, select **Hardware and Sound** and then select **Power Options**.
3.  Select **Create a power plan.**
4.  In the **Plan name** box, enter **Power Save - Presentation** and select **Next**.
5.  Select **Create**.
6.  Under **Preferred plans**, next to **Power Save - Presentation**, select **Change plan settings**.
7.  Select **Change advanced power settings**.
8.  Expand **Hard disk** and then expand **Turn off hard disk after**. Change the setting to **60** minutes.
9.  Scroll down and expand the **Multimedia settings** option.
10.  Expand the **When playing video** option and change the setting to **Balanced**.
11.  Select **OK** to close the **Power Options** dialog box.
12.  Close all open windows.

**Results:** After finishing this exercise you will have configured computer settings using Windows Settings and the Control Panel.

## Exercise 2: Using PowerShell to Configure Windows

### Scenario

You need to use Windows PowerShell to test the scripting environment. To become familiar with PowerShell you will run several commands and the use PowerShell ISE to create a script to list all running services on the device.

### Task 1: Use Windows PowerShell to configure a device

1.  Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd.**

2.  Select **Start** and type **PowerShell**. Select **Run as Administrator**. 

3.  At the PowerShell window, type the following and then press **Enter**:

```
Get-ExecutionPolicy
```

4.  Confirm the current setting of the PowerShell execution policy is set to **Restricted.**

5.  If the execution policy is set to **Restricted**, change it to **Unrestricted** by running the following command at the PowerShell window:

```
Set-ExecutionPolicy Unrestricted
```

6.  Confirm that the execution policy is now **Unrestricted**.

7.  At the PowerShell window, launch Notepad by typing the following command and then press **Enter**:

```
Start-Process Notepad
```

8.  At the PowerShell window, type the following command and then press **Enter**:

```
Get-Process
```

9.  Review the list of all running processes. Identify that Notepad is running and note the Process ID.

10.  At the PowerShell window, type the following command and then press **Enter**. Replace [ID] with the Process ID identified in step 9.

```
Stop-Process -Id [ID]
```

11.  Verify that the Notepad window is no longer open.

12.  At the PowerShell window, list the application log entries by typing the following command and then press **Enter**:

```
Get-EventLog -LogName "Application"
```

12.  Select **Start** and type **Telnet**. Select **Turn Windows features on and off**.

13.  In the **Windows Features** window, verify that **Telnet Client** is not selected.

14.  At the PowerShell Window, type the following command, and then press **Enter**:

```
Enable-WindowsOptionalFeature -Online -FeatureName "TelnetClient"
```

_Note: This will install the Telnet Client windows feature._

15.  Select **Start** and type **Telnet**. Select **Open**.

16.  Close all open windows.


### Task 2: Use a Windows PowerShell Script

1. In the **Type here to search** box, type **\\\SEA-DC1\\Labfiles** and then press Enter.

2. In the content pane, double-click the **Configure** folder.

3. Copy the **Services.ps1** file into the **E:\\Labfiles** folder on SEA-CL1.

4. Select **Start** and type **Powershell ISE**. Press **Enter**.

5. In the Windows PowerShell ISE, open the script file **E:\\Labfiles\\Services.ps1**.

6. Read the script, and then note what the script is doing, according to the following note.

   -   _Note:_
   -   _Comments are green._
   -   _Variables are red._
   -   _Cmdlets are bright blue._
   -   _Text in quotation marks is dark red._

7. Select line 3 in the script, and then select **Run selection (F8)**.

   _Note: Only the command in line 3 will be executed._

8. Select **Run script (F5)**, and then read the output.

   _Note: The output does not have multiple colors._

9. At the end of line 14, type **–ForegroundColor \$color**

10. On the toolbar, select **Run script (F5)** in the Windows PowerShell ISE window. Select **OK** to save the file, and then read the output.

    _Note: Running services are green, and services that are not running are red._

11. On line 16, type **Write-Host "A total of" \$services.count "services were evaluated"**

12. Select **Run script (F5)**, and in the Windows PowerShell ISE window select **OK**.

13. Select **Show Command Add-on** in the PowerShell ISE toolbar.

14. In the **Commands** pane, select the **Write-Host** cmdlet and then configure the following options:

    -   BackgroundColor: **Gray**

    -   ForegroundColor: **Black**

    -   Object: **"Script execution is complete"**

15. Select **Copy** and paste the command to line 17 of the script.

16. Select **Run script (F5)**, and in the Windows PowerShell ISE window select **OK**.

17. Select **Start** and type **PowerShell**. Press **Enter**.

18. At the PowerShell window, type the following command and then press **Enter**:

```
Set-Location E:\Labfiles
```

13. At the PowerShell window, type the following and then press **Enter**:

```
.\Services.ps1
```

14. Close all open windows and sign out of SEA-CL1.

**Results:** After completing the exercise you have learned how to manage Windows 10 using PowerShell and PowerShell scripts.

## Exercise 3: Customizing the Start Layout in Windows 10

### Scenario

You need to ensure that all Windows 10 devices contain the Contoso utilities apps on the Start menu. To do this, you decide to create and export a custom Start layout that only locks down the specified groups in the XML file. Users will still be able to customize other areas of the Start menu as needed.

### Task 1: Customize the Start screen

1.  Sign in to **SEA-CL1** as **.\\Admin** with the password **Pa55w.rd.** This signs in as the local administrator on the device.
2.  Select **Start**, and right-click each tile and then select **Unpin from Start**.
3.  From the Start menu, right-click each of the following apps and then select **Pin to Start:**
    - Snip & Sketch
    - Sticky Notes
    - Voice Recorder
    - Calculator
    - Alarms & Clock
    - Maps
4.  In the Start screen, just above the tiles, click and select **Name group** and then replace the text with **Contoso Utilities**. 
5.  Close the Start menu.

### Task 2: Export the Start layout

1. On SEA-CL1, right-click the Start menu and then select **Windows PowerShell (Admin)**. Select **Yes** at the User Account Control.

2. At the PowerShell window, type the following command and then press **Enter**:

```
Export-StartLayout -UseDesktopApplicationID -Path E:\Labfiles\ContosoLayout.xml
```

3. Open **File Explorer** and then browse to **E:\\Labfiles**.
4. Right-click **ContosoLayout.xml**, point to **Open with** and then select **Notepad**.
5. At the first instance of **\<DefaultLayoutOverride>**, type the following:

```
<DefaultLayoutOverride LayoutCustomizationRestrictionType="OnlySpecifiedGroups">
```

6. Save the **ContosoLayout.xml** file and then close Notepad.
7. Close all open windows and sign out of SEA-CL1.

### Task 3: Deploy the Start layout using Group Policy

1. Sign in to SEA-CL1 as **Contoso\\Administrator** with the password of **Pa55w.rd**.
2. Open **File Explorer** and then browse to **E:\\Labfiles**.
3. Right-click **ContosoLayout.xml**, and then Copy the file.
4. In the Address bar, browse to **\\\\SEA-DC1\\Netlogon**.
5. Paste **ContosoLayout.xml** into the **Netlogon** folder and then close File Explorer.
6. Sign out of SEA-CL1.
7. Switch to SEA-SVR1.
8. If necessary, sign in to SEA-SVR1 as **Contoso\\Administrator** with the password of **Pa55w.rd**.
9. Select **Start** and then select **Server Manager**.
10. Select **Tools** and then select **Group Policy Management**.
11. Maximize the Group Policy window. In the console tree, expand **Forest:Contoso.com**, expand **Domains**, and then expand **Contoso.com**. Select the **Group Policy Objects** node.
12. Right-click the **Group Policy Objects** node, and then select **New**.
13. In the **New GPO** dialog box, in the **Name** box, type **Win10StartLayout**, and then select **OK**.
14. In the details pane, right-click **Win10StartLayout**, and then select **Edit**. Maximize the Group Policy Management Editor window.
15. In the console tree, under **User Configuration**, expand **Policies**, expand **Administrative Templates**, and then select **Start Menu and Taskbar**.
16. Double-click **Start Layout**.
17. In the **Start Layout** box, select **Enabled** and then under **Start Layout File** enter **\\\\SEA-DC1\\Netlogon\\ContosoLayout.xml**. Click **OK** and then close the **Group Policy Management Editor**.
18. In the Group Policy Management console, right-click **Sales** and then select **Link an Existing GPO**.
19. From the **Select GPO** box, select **Win10StartLayout** and then select **OK**.
20. Close the Group Policy Management console.

### Task 4: Verify the Windows 10 Start layout

1. Switch to SEA-CL1.
2. Sign in to SEA-CL1 as **Contoso\\Reda** with the password of **Pa55w.rd**.
3. Select **Start** and then take note of the Start page. The **Contoso Utilities** group displays a lock icon that specifies that the group cannot be modified. 
4. In the Start menu, right-click **Word** and then select **Pin to Start**. Notice that you can still customize other sections of the Start page.
5. Sign out of SEA-CL1.

**Results:** After completing the exercise you have learned how to customize and deploy a custom Windows 10 Start layout.

**END OF LAB**
