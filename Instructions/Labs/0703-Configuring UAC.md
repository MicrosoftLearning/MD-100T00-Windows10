# Practice Lab: Configuring UAC

## Summary

In this lab you will learn how to modify the settings for the User Account
Control.

### Scenario

You are interested in configuring UAC so that when the UAC dialog box prompts a
standard user, he or she can enter the credentials of an administrator account
to gain elevated privileges. You also want to restrict the execution of unsigned
applications.


### Task 1: Modify UAC prompts

1.  Sign in to **LON-CL1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

2.  In the **Type here to search** box on the taskbar, type **gpedit.msc**, and
    then press Enter.

3.  In the Local Group Policy Editor, expand **Computer Configuration**, expand
    **Windows Settings**, expand **Security Settings**, expand **Local
    Policies**, and then select **Security Options**.

4.  In the results pane, double-click **User Account Control: Behavior of the
    elevation prompt for standard users**.

5.  In the **User Account Control: Behavior of the elevation prompt for standard
    users** dialog box, select the **Prompt for credentials** drop down list,
    select **Prompt for credentials on the secure desktop**, and then select
    **OK**.

6.  In the results pane, double-click **User Account Control: Only elevate
    executables that are signed and validated**.

7.  In the **User Account Control: Only elevate executables that are signed and
    validated** dialog box, select **Enabled**, and then select **OK**.

8.  In the results pane, double-click **User Account Control: Behavior of the
    elevation prompt for administrators in Admin Approval Mode**.

9.  In the **User Account Control: Behavior of the elevation prompt for
    administrators in Admin Approval Mode** dialog box, select the **Prompt for
    consent for non-Windows binaries** drop down list, select **Prompt for
    consent on the secure desktop**, and then select **OK**.

10. Close the Local Group Policy Editor.

11. Sign out of **LON-CL1**.


### Task 2: Test the UAC prompts as a standard user

1.  Sign in to **LON-CL1** as **Adatum\\Beth** with the password **Pa55w.rd**.

2.  Right-click **Start**, and then select **Windows PowerShell (Admin)**.  
    
    _**Note**: The Windows operating system displays the User Account Control
    prompt._

3.  In the **User name** box, type **Administrator**, and in the **Password**
    box, type **Pa55w.rd**, and then select **Yes**.

4.  Close the Windows PowerShell prompt.

5.  Sign out of **LON-CL1**.

 

### Task 3: Test the UAC prompts as an administrator

1.  Sign in to **LON-CL1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

2.  In the **Type here to search** box on the taskbar, type **Control Panel**,
    and then press Enter.

3.  In Control Panel, select **System and Security**.

4.  In **System and Maintenance**, select **Change User Account Control
    settings**.

5.  Verify that the slider is configured for **Always notify**.

6.  Select **Cancel**.

7.  Close all open windows.


**Results**: After completing this exercise you have configured the prompt
behavior of UAC.

**END OF LAB**