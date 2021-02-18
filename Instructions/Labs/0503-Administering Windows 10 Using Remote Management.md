# Practice Lab: Administering Windows 10 Using Remote Management 

## Summary

In this lab you will learn how to perform remote Windows administration using Remote PowerShell, Remote Desktop, and Windows Admin Center.

## Exercise 1: Administering Windows using Remote PowerShell and Remote Desktop

### Scenario

Your company is planning to open a new branch office. To manage the devices in the new branch office you need to use Remote PowerShell and Remote Desktop. You need to test remote administration by running remote PowerShell commands on SEA-SVR2 and you need to enable Remote Desktop on SEA-CL1.

### Task 1: Perform remote management using Windows PowerShell

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password: **Pa55w.rd**.

2. Right-click **Start**, and then select **Windows PowerShell**.

3. To view all of the services that are stopped on SEA-SVR2, in the Windows PowerShell window, type the following command, and then press **Enter**:

   ```
   Get-Service -ComputerName SEA-SVR2 | Where-Object {$_.Status -eq "Stopped"}
   ```

4. To view the the content of the C:\\Program Files folder on SEA-SVR2, in the Windows PowerShell window, type the following command, and then press **Enter**:

   ```
   Invoke-Command -ComputerName SEA-SVR2 -ScriptBlock {Get-ChildItem "C:\Program Files"}
   ```

5. To view the the System event log on SEA-SVR2, in the Windows PowerShell window, type the following command, and then press **Enter**:

   ```
   Invoke-Command –ComputerName SEA-SVR2 –ScriptBlock {Get-EventLog –log system}
   ```


6. To determine if the WinRM service is running on SEA-SVR2, in the Windows PowerShell window, type the following command, and then press **Enter**:

   ```
   Test-WsMan SEA-SVR2
   ```

   *Note: The output on SEA-SVR2 validates that the WinRM service is running and it is ready to receive WS-Management requests. If it was not configure, you would have needed to run **Winrm quickconfig** on SEA-SVR2.* 

7. In the Windows PowerShell window, type the following commands, and then press **Enter** after each one:

   ```
   Enter-PSSession SEA-SVR2
   Get-command
   Add-Content Remote.txt "Adding text to file on SEA-SVR2"
   Exit-PSSession
   ```


### Task 2: Enable Remote Desktop

1.  On **SEA-CL1**, select **Start**, and then select the **Settings** icon.
2.  In **Settings**, select **System**.
3.  On the **System** tab, select **Remote Desktop**.
4.  Switch **Enable Remote Desktop** on.
5.  In the Remote Desktop Settings window select **Confirm**.
6.  On the Remote Desktop page, select **Advanced settings**.
7.  Verify that Require computers to use Network Level Authentication to connect is selected. Also take note of the Current Remote Desktop Port, which is set to 3389.
8.  Close the Settings page and close Windows PowerShell.

**Results**: After completing this exercise, you will have enabled and tested remote PowerShell and Remote Desktop.

## Exercise 2: Administering Windows using Windows Admin Center

### Scenario

You need to test remote administration capabilities of the Windows Admin Center. For this scenario, you will install Windows Admin Center on SEA-CL1 and then perform remote administration tasks on SEA-SVR1. 

### Task 1: Install Windows Admin Center

1.  Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password: **Pa55w.rd**.
2.  On the taskbar, select **File Explorer**.
3.  In File Explorer, browse to **E:\\Labfiles\\Tools**, and then double-click **WindowsAdminCenter2009.msi**. Windows Installer begins the installation process.
4.  On the **Windows Admin Center Setup** license page, select the check box next to **I accept these terms**, and then select **Next**.
5.  Select **I don't want to use Microsoft Update**, and then select **Next**.
6.  On the **Configure Gateway Endpoint** page, select **Next**. 
7.  On the **Installing Windows Admin Center** page, configure the following and then select **Install**:
    - Select a port for the Windows Admin Center site: **6516**
    - Allow Windows Admin Center to modify this machine's trusted hosts settings: **Selected**
    - Create a desktop shortcut to launch Windows Admin Center: **Selected**.
8.  On the **One more thing** page, take note of the message and then select **Finish**.
9.  Close File Explorer.

### Task 2: Add connections to Windows Admin Center

1.  On **SEA-CL1**, on the desktop, double-click the **Windows Admin Center** icon.
2.  In the **Select a certificate for authentication** window, select **OK**.
3.  On the **All connections** page, select **Add**.
4.  On the **Add or create resources** page, in the **Servers** pane, select **Add**.
5.  On the **Add one** tab, under **Server name**, type **SEA-SVR1**. Windows Admin Center queries Active Directory and then displays the server. 
6.  Select **Add** to add SEA-SVR1.Contoso.com to the All connections page.

### Task 3: Perform Remote Administration using Windows Admin Center

1.  In the **Windows Admin Center**, select **SEA-SVR1.Contoso.com**.
2.  On the **Overview** page, take note of the server information and performance statistics.
3.  On the **Tools** pane, select **Events**.
4.  On the **Events** pane, take note of the event logs that are available from SEA-SVR1 and then under **Windows Logs** select **System**.
5.  Review the System log events and then select the **Clear** button.
6.  On the **Clear** prompt, select **Clear log**.
7.  On the **Tools** pane, select **Files & file sharing**.
8.  In the details pane, on the **File explorer** tab, take note of the file structure from SEA-SVR1.
9.  In the details pane, select the **File share** tab. Take note of the current shared folders.
10.  On the **Tools** pane, select **Local users & groups**. Take note of the Users and Groups tabs where you can manage local users and groups on SEA-SVR1.
11.  On the **Tools** pane, select **PowerShell**. A remote PowerShell session is established to SEA-SVR1.
12.  In the PowerShell pane, type `Get-Service` and then press Enter. SEA-SVR1 services are displayed.
13.  On the **Tools** pane, select **Remote Desktop**. On the **Navigating away closes PowerShell** box, select **Continue**. 
14.  On the **Remote Desktop** page, read the message and then select **Go to settings**.
15.  On the **Settings** page, select **Remote Desktop** and then under **Remote Desktop** select **Allow remote connections to this computer**. Select **Save**.
16.  On the **Tools** pane, select **Remote Desktop**. 
17.  On the **Do you want to connect using the certificate presented by sea-svr1.contoso.com** prompt, select **Connect**.
18.  On the **Enter credentials for the Remote Desktop connection**, type Username **Contoso\Administrator** with the Password of **Pa55w.rd**. Select **Connect**. The SEA-SVR1 desktop displays in the Remote Desktop pane.
19.  Select **Disconnect**.
20.  On the **Tools** pane, select **Roles & features**. Notice that you can remotely install or uninstall server roles and features on SEA-SVR1.
21.  Close Windows Admin center and then sign out of SEA-CL1.

**Results**: After completing this exercise, you will have installed Windows Admin Center on SEA-CL1 and then performed remote administration tasks on SEA-SVR1.

**END OF LAB**