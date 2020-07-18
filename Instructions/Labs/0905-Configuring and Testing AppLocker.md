# Practice Lab: Configuring and Testing AppLocker

## Summary

In this exercise you will learn how to configure AppLocker.

### Scenario

A manager has requested that Windows Media Player cannot be launched by his team
on LON-CL1, however members of the IT group still require the ability to do so.
You decide to use AppLocker.

 

### Task 1: Create a new executable rule

1.  Sign in to **LON-CL1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

2.  In the **Type here to search** box on the taskbar, type **gpedit.msc**, and
    then press **Enter**.

3.  In the Local Group Policy Editor, expand **Computer Configuration**, expand
    **Windows Settings**, expand **Security Settings**, expand **Application
    Control Policies**, expand **AppLocker,** and then select **Executable
    Rules**,

4.  In the details pane, right-click the empty space and then select **Create
    New Rule**.

5.  In the **Create Executable Rules** Wizard, select **Next**.

6.  On the **Permissions** page, select **Deny**, and then select **Select**.

7.  In the **Select User or Group** dialog box, in the **Enter the object name
    to select (examples)** box, type **IT**, select **OK**, and then select
    **Next**.

8.  On the **Conditions** page, select **Path**, and then select **Next**.

9.  On the **Path** page, select **Browse Files**, in the **File name** box,
    type **C:\\Program Files\\Windows Media Player\\wmplayer.exe**, and then
    select **Open**.

10. Select **Next** twice, and then select **Create**.

11. Select **Yes** when prompted to create default rules.

12. In the navigation pane, Select **Packaged app Rules**.

13. In the details pane, right-click the empty space and then select **Create
    Default Rules**.



### Task 2: Enforce AppLocker rules

1.  In the Local Group Policy Editor, right-click **AppLocker**, and then select
    **Properties**.

2.  On the **Enforcement** tab, under Executable rules, select the
    **Configured** check box, select **Enforce rules**, and then select **OK**.

3.  Close the Local Group Policy Editor.

4.  Right-click **Start**, and then select **Windows PowerShell**.

5.  At the Windows PowerShell prompt, type the following command, and then press
    **Enter**:

    ```
    gpupdate /force
    ```


### Task 3: Confirm executable rule enforcement

1.  Right-click **Start**, and then select **Computer Management**.

2.  In **Computer Management**, expand **Services and Applications**, and then
    select **Services.**

3.  Right-click the **Application Identity** service, and then select **Start**.

4.  Wait two minutes to allow the AppLocker policy to apply.

5.  Expand **Event Viewer**, expand **Applications and Services Logs**, expand
    **Microsoft**, expand **Windows**, expand **AppLocker**, and then select
    **EXE and DLL**.

6.  Review the entries in the results pane. Locate **Event ID 8001.**  
    **Note**: This will show that the AppLocker Policy is active now.

7.  Sign out of **LON-CL1**.

   

### Task 4: Test rule enforcement

1.  Sign in to **LON-CL1** as **Adatum\\Beth** with the password **Pa55w.rd**.

2.  In the **Type here to search** box on the taskbar, type **Media Player**,
    and then select **Windows Media Player**.

    _**Note**: You will be unable to start Windows Media Player._

1.  In the **This app has been blocked by your system administrator** dialog
    box, select **Close**.

2.  Right-click **Start**, and then select **Event Viewer**.

3.  In Event Viewer, expand **Applications and Services Logs**, expand
    **Microsoft**, expand **Windows**, expand **AppLocker**, and then select
    **EXE and DLL**.

4.  Review the entries in the results pane. Locate **Event ID 8004**. One of
    them show that Beth attempted to run a prohibited application.

5.  Close Event Viewer.

6.  Sign out of **LON-CL1**.


**Results**: After completing this exercise, you should have configured an
AppLocker policy to prevent users from starting Windows Media Player.

**END OF LAB**