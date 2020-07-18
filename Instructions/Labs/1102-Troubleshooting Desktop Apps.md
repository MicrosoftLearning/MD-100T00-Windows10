# Practice Lab:  Troubleshooting Desktop Apps  

## Summary
During this lab you will learn how to troubleshoot AppLocker policies.

### Scenario
Your manager has come to you indicating that there are reports of staff in
one department who are installing unauthorized programs. Your manager
indicates that the AppLocker policies in place should be preventing this.
You need to investigate why they are not working. \\\\lon-dc1\\labfiles\\Apps\\XmlNotepad.msi is available to test as an app that should not be possible to install. 

### Task 1: Review the help-desk Incident Record  ###

1.  Read the Additional Information section of the incident record in the
    Student Handbook exercise scenario.


| Incident Reference Number: 723401                 |
|-----------------------------------|
| **Incident Reference Number**: 723401 <br> **Date of Call:** January 4 <BR> **User:** Alan Steiner (Marking Dept) <BR>**Status:** Open|
| **Incident Details**<br> Users are installing unauthorized applications in the Marketing department.  |
| **Additional Information**<br> Alan Steiner, one of the marketing managers, has reported that users are installing unauthorized desktop apps. <br>The AppLocker policies that are in place do not appear to be working.<br>You must determine why these policies are not being enforced. |
| **Plan of Action**                |
| **Resolution**                    |       


      
### Task 2: Verify the problem 

1.  Switch to **LON-CL1**.

2.  Sign in by using the following credentials:
-   User name: **Adatum\\Benjamin**
-   Password: **Pa55w.rd**

3.  On the desktop, on the taskbar, select the **File Explorer** icon.

4.  In the File Explorer address bar, type
    **\\\\lon-dc1\\labfiles\\Apps\\XmlNotepad.msi**, and then press **Enter**.

5.  When installation starts, cancel it by selecting **Cancel,** then select
    **Yes,** then **Finish.**

    _**Note**: This step shows that the AppLocker policy is not being enforced._

### Task 3: Attempt to resolve the problem with an App Locker policy

1.  Switch to **LON-DC1**.

2.  **Sign in** to LON-DC1 as **Adatum\\Administrator** with the password of
    **Pa55w.rd**.

3.  On LON-DC1, in the Server Manager window, select **Tools**, and then select
    **Group Policy Management**.

4.  In the Group Policy Management window, expand **Forest: Adatum.com**,expand
    **Domains**, expand **Adatum.com**, and then select **Marketing**.

5.  Right-click **Marketing**, and then select **Create a GPO in this domain
    and link it here**. Name the new GPO **Marketing** and select **OK**. Right-click the **Marketing** GPO and select **Edit**.

6.  In the Group Policy Management Editor window, expand **Computer
    Configuration**, expand **Policies**, expand **Windows Settings**, expand
    **Security Settings**, expand **Application Control Policies**, expand
    **AppLocker**, and then select **Windows Installer Rules**.

7.  Right-click **Windows Installer Rules**, and then select **Create Default
    Rules**.

8.  Right-click **Windows Installer Rules**, and then select **Create New Rule**.

9.  On the Before You Begin page, select **Next**.

10. On the Permissions page, select **Deny**, and then select **Next**.

11. On the Conditions page, select **Path**, and then select **Next**.

12. On the Path page, select **Browse Files**.

13. In the File name text box, type **\\\\lon-dc1\\labfiles\\apps**, and then
    press **Enter**.

14. In the Open dialog box, double-click **XmlNotepad.msi**, and then select
    **Next**.

15. On the Exceptions page, select **Next**, and then select **Create**.

16. In the navigation pane, right-click **AppLocker**, and then select
    **Properties**.

17. In the AppLocker Properties dialog box, under Windows Installer rules,
    select the **Configured** check box, and then select **OK**.

18. In the navigation pane, select **System Services**, and then double-click
    **Application Identity**.

19. In the Application Identity Properties dialog box, select the **Define this
    policy setting** check box, select **Automatic**, and then select **OK**.

20. **Close** the Group Policy Management Editor window.

21. Close Group Policy Management.
	
### Task 4: Apply the AppLocker policy

1.  In the Server Manager window, select **Tools**, and then select **Active
    Directory Users and Computers**.

2.  In Active Directory Users and Computers, expand **Adatum.com**, and then
    select **Computers**.

3.  Right-click **LON-CL1**, and then select **Move**.

4.  In the Move dialog box, select **Marketing**, and then select **OK**.

5.  Switch to **LON-CL1** and restart LON-CL1.

6.  Sign in to **LON-CL1** using the following credentials:
    -   User name: **Adatum\\Benjamin**
    -   Password: **Pa55w.rd**

7.  On the desktop, on the taskbar, select the **File Explorer** icon.

8.  In the File Explorer address bar, type
    **\\\\lon-dc1\\labfiles\\Apps\\XmlNotepad.msi**, and then press **Enter**.

9.  In the Windows Installer dialog box, select **OK**.

10. Sign out of **LON-CL1**.

11. Update the Resolution section of the incident record with the following
    comments:
- Enabled Default Windows Installer rules.
- Verified the installer path in the Deny rule.
- Turned on AppLocker enforcement.
- Configured policy to start the Application Identity service.
- Moved a computer, LON-CL1, to Marketing OU to test the policy.

**Results**: After completing this exercise, you should have successfully resolved the AppLocker policy application problem.

**END OF LAB**