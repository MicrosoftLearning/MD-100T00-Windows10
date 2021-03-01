#  Practice Lab: Work Folders

## Summary

In this lab you will learn how to configure Work Folders as a method of synchronizing files to provide access from multiple devices.

### Scenario

Members of the Marketing group often use multiple devices for their work. To help manage file access you decide to implement Work Folders. This allows for files to be stored in a central location and synchronized to each device automatically. To implement this solution, first you will install and configure the Work Folders server role on SEA-SVR1 and store the content in a shared folder named C:\\syncshare1. To enable the Work Folders for all marketing users, you configure a Group Policy Object to point to <https://SEA-SVR1.Contoso.com>. You have asked Bruce Keever to test the solution on a domain-joined device named SEA-CL1 and a stand-alone device named SEA-WS3. Bruce will validate synchronization and identify how synchronization conflicts are handled. 

### Task 1: Install and Configure Work Folders

1.  Sign in to **SEA-SVR1** as **Contoso\\Administrator** with the password **Pa55w.rd**.
    
2.  Right-click **Start**, and then select **Windows PowerShell (Admin)**.

3. In Windows PowerShell, type the following cmdlet, and then press **Enter**:

   ```
   Install-WindowsFeature FS-SyncShareService
   ```

   _**Note**: After the feature installs, you might see a warning display, because Windows automatic updating is not enabled. For the purposes of this lab, ignore the warning._

4. In Windows PowerShell, type the following cmdlet, and then press **Enter**:

   ```
   Start-Service SyncShareSvc
   ```

5. Close the **Windows PowerShell** window.

6. Select **Start**, and then select **Server Manager**.

7. In Server Manager, in the navigation pane, select **File and Storage Services**, and then select **Work Folders**.

8. In the **WORK FOLDERS** section, select **TASKS**, and then select **New Sync Share**.

9. In the **New Sync Share Wizard**, on the **Before you begin** page, select **Next**.

10. On the **Select the server and path** page, in the **Enter a local path** text box, type **C:\\syncshare1**, select **Next**.

    _**Important:** If **SEA-SVR1** is not listed in the **Server** section, select **Cancel**. In Server Manager, select **Refresh**, and then repeat this task, beginning with step 6 and completing the remaining steps. This may take a few minutes for SEA-SVR1 to show._    

11. In the New Sync Share Wizard dialog select **OK**.

12. On the **Specify the structure for user folders** page, verify that **User alias** is selected, and then select **Next**.

13. On the **Enter the sync share name** page, select **Next** to accept the default sync share name.

14. On the **Grant sync access to groups** page, select **Add**, and in the **Enter the object name to select** text box, type **Marketing**. select **OK**, and then select **Next**.

15. On the **Specify security policies for PCs** page, verify the two available options. Clear the **Automatically lock screen, and require a password** check box, and then select **Next**.

16. On the **Confirm selections** page, select **Create**.

17. On the **View Results** page, select **Close**.

18. In Server Manager, in the **WORK FOLDERS** section, verify that **syncshare1** is listed, and that in the **USERS** section, the user **Bruce Keever** is listed.

19. On **SEA-SVR1**, in Server Manager, select **Tools**, and then select **Internet Information Services (IIS) Manager**.

20. In the Microsoft Internet Information Services (IIS) Manager, in the navigation pane, expand  **SEA-SVR1 (Contoso\\Administrator)**. Expand **Sites**, right-click **Default Web Site**, and then select **Edit Bindings**.

21. In the **Site Bindings** dialog box, select **Add**.

22. In the **Add Site Binding** dialog box, in the **Type** box, select **https**. In the **SSL certificate** box, select **Work Folders Cert**, select **OK**, and then select **Close**.

23. Close the IIS Manager.   

### Task 2: Create a GPO to deploy the Work Folders 

1.  On **SEA-SVR1**, in Server Manager, select **Tools,** and then select **Group Policy Management**.
2.  In the Group Policy Management console, in the navigation pane, expand **Forest: Contoso.com**, expand **Domains**, expand **Contoso.com**, and then select the **Marketing** organizational unit (OU). 
3.  Right-click **Marketing**, and then select **Create a GPO in this domain, and Link it here**. In the **Name** text box, type **Deploy Work Folders**, and then select **OK**.
4.  Right-click **Deploy Work Folders**, and then select **Edit**.
5.  In the Group Policy Management Editor, in the navigation pane expand **User Configuration**, expand **Policies**, expand **Administrative Templates**, expand **Windows Components**, and then select **Work Folders**.
6.  In the details pane, right-click **Specify Work Folder settings**, and then select **Edit**.
7.  In the **Specify Work Folder settings** dialog box, select **Enabled**. In the **Work Folders URL** text box, type <https://SEA-SVR1.Contoso.com>, select the **Force automatic setup** check box, and then select **OK**.
8.  Close the Group Policy Management Editor and the Group Policy Management console.
9.  Close Server Manager.


### Task 3: Test the work folders

1.  Switch to **SEA-CL1**.

2.  Sign in to **SEA-CL1** as **Contoso\\Bruce** with the password **Pa55w.rd**.
    
3.  Select the **File Explorer** icon on the taskbar.

4.  In the navigation pane, select **Work Folders**. 

5.  In the details pane right-click the empty space, select **New**, select **Text Document**, and then name the file **On SEA-CL1**.
    
6.  Select **Start**, type **Work folders** and select **Manage Work Folders**.

7.  On the Manage Work Folders page, check the option **Sync files over metered connections**.
    
    _**Note**: This is only needed due to the hosted lab environment configuration._    

8.  Close the **Manage Work Folders** window.

9.  Switch to **SEA-WS3**.

10.  Sign in to **SEA-WS3** as **SEA-WS3\\Admin** with the password **Pa55w.rd**.

11.  On **SEA-WS3** select **Start**, type **\\\\SEA-DC1\\certenroll**, and then press **Enter**.
    
12.  In the **Enter Network credentials** dialog box, enter the user name as **Contoso\\Administrator** and the password as **Pa55w.rd**. Select **OK**.
    
13.  In the **certenroll** window, double-click **SEA-DC1.Contoso.com_ContosoCA.crt.**
    
14.  On the **Certificate** dialog box, select **Install Certificate**.

15.  On the **Certificate Import Wizard**, select **Local Machine** and select **Next**.
    
16.  On the **User Account Control** dialog box, select **Yes**.

17. On the **Certificate Store** page, select **Place all certificates in the following store**, and then select **Browse**.
    
18. On the **Select Certificate Store** page, select **Trusted Root Certification Authorities** and select **OK**.
    
19. On the **Certificate Store** page, select **Next**.

20. On the **Certificate Import Wizard** page, select **Finish**.

21. In the **Certificate Import Wizard** dialog select **OK**, and then in the **Certificate** window, select **OK**.
    
22. Restart **SEA-WS3**.

23. Sign in to **SEA-WS3** as **SEA-WS3\\Admin** with the password **Pa55w.rd**.

24. On **SEA-WS3**, select **Start**, type **Control Panel**, and then press Enter.
    
25. In Control Panel, select **System and Security,** and then select **Work Folders**.
    
26. On the **Manage Work Folders** page, select **Set up Work Folders**.

27. On the **Enter your work email address** page, select **Enter a Work Folders URL instead**.
    
28. On the **Enter a Work Folders URL** page, in the **Work Folders URL** text box, type <https://SEA-SVR1.Contoso.com>, and then select **Next**.
    
29. In the **Windows Security** dialog box, in the **User name** text box, type **Contoso\\Bruce**, and in the **Password** text box, type **Pa55w.rd**, and then select **OK**.
    
30. On the **Introducing Work Folders** page, review the local Work Folders location, and then select **Next**.
    
31. On the **Security policies** page, select the **I accept these policies on my PC** check box, and then select **Set up Work Folders**.
    
32. On the **Work Folders has started syncing with this PC** page, select **Close**.
    
33. Switch to the Manage Work Folders window.

34. On the Manage Work Folders window, check the option **Sync files over metered connections**.
    
    _**Note**: This is only needed due to the hosted lab environment configuration._    

35.  Switch to the Work Folders File Explorer window.

36.  Verify that the **On SEA-CL1.txt** file displays.

37. Right-click in the details pane, select **New**, select **Text Document**, and then in the **Name** text box, type **On SEA-WS3**, and then press **Enter**. 

### Task 4: Test conflict handling

1.  Switch to **SEA-CL1**.

2.  On **SEA-CL1**, in **Work Folders**, verify that that both files, **On SEA-CL1** and **On SEA-WS3**, display. 
    
3.  In the notification area, right-click the connection icon, and then select **Open Network & Internet settings**.
    
4.  Select the Ethernet page, and then select **Change adapter options**. 

5.  Right-click **Ethernet**, and then select **Disable**. In the **User Account Control** dialog box, in the **User name** text box, type **Administrator**. In the **Password** text box, type **Pa55w.rd**, and then select **Yes**.
    
6.  In **Work Folders**, double-click the **On SEA-CL1** file.

7.  In Notepad, type **Modified offline**, press Ctrl+S, and then close Notepad .
    
8.  In **Work Folders**, right-click in the details pane, select **New**, select **Text Document**, and then name the file **Offline SEA-CL1**.
    
9.  Switch to **SEA-WS3.**

10. On **SEA-WS3**, in **Work Folders**, double-click the **On SEA-CL1.txt** file.
    
11. In Notepad, type **Online modification**, press Ctrl+S, and then close Notepad.
    
12. Switch to **SEA-CL1.**

13. On **SEA-CL1**, in the **Network Connections** window, right-click **Ethernet**, and then select **Enable**. 
    
14. In the **User Account Control** dialog box, in the **User name** text box, type **Administrator**, and in the **Password** text box, type **Pa55w.rd**, and then select **Yes**.
    
15. Switch to **Work Folders**, and then verify that files display in the details pane, including **On SEA-CL1** and **On SEA-CL1-SEA-CL1**.
    
    _Note: Because you modified the file at two locations, a conflict occurred, and one of the copies was renamed._    
16.  Sign out from **SEA-CL1** and **SEA-WS3**.

**Results**: After finishing this lab you have installed and configured Work Folders.

### Lab cleanup

1. Sign in to **SEA-SVR1** as **Contoso\\Administrator** with the password **Pa55w.rd**.

2. Right-click **Start**, and then select **Windows PowerShell (Admin)**.

3. In Windows PowerShell, type the following cmdlet, and then press **Enter**:

   ```
   Remove-WindowsFeature FS-SyncShareService
   ```

   _**Note**: The feature will be removed and requires a restart of the server._

4. In Windows PowerShell, type the following cmdlet, and then press **Enter**:

   ```
   Restart-Computer
   ```


**END OF LAB**
