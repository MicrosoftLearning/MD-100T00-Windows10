# Practice Lab:  Troubleshooting Desktop Apps  

## Summary

During this lab you will learn how to troubleshoot AppLocker policies.

### Scenario

Your manager has come to you indicating that there are reports of staff in
one department who are installing unauthorized programs. Your manager
indicates that the AppLocker policies in place should be preventing this.
You need to investigate why they are not working. \\\\lon-dc1\\labfiles\\Apps\\XmlNotepad.msi is available to test as an app that should not be possible to install.

### Task 1: Review the help-desk Incident Record

1. Read the Additional Information section of the incident record in the
    Student Handbook exercise scenario.

| Incident Reference Number: 723401 ||
|-----------------------------------|:---|
| **Incident Reference Number**| 723401 |
| **Date of Call**             | January 4 |
| **User**                     | Alan Steiner (Marketing Dept) |
| **Status**                   | Open |
| **Incident Details**         | Users are installing unauthorized applications in the Marketing department.|
| **Additional Information**   | Alan Steiner, one of the marketing managers, has reported that users are installing unauthorized desktop apps. The AppLocker policies that are in place do not appear to be working. You must determine why these policies are not being enforced. |
| **Plan of Action**           |
| **Resolution**               |

### Task 2: Verify the problem

1. Switch to **LON-CL1**.

 Sign in by using the following credentials:
    - User name: **Adatum\\Benjamin**
    - Password: **Pa55w.rd**

1. On the desktop, on the taskbar, select the **File Explorer** icon.

1. In the File Explorer address bar, type
    **\\\\lon-dc1\\labfiles\\Apps\\XmlNotepad.msi**, and then press **Enter**.

1. When installation starts, cancel it by selecting **Cancel,** then select
    **Yes**, then **Finish.**

     _**Note**: This step shows that the AppLocker policy is not being enforced._

### Task 3: Attempt to resolve the problem with an App Locker policy

1. Switch to **LON-DC1**.

1. **Sign in** to LON-DC1 as **Adatum\\Administrator** with the password of
    **Pa55w.rd**.

1. On LON-DC1, in the Server Manager window, select **Tools**, and then select
    **Group Policy Management**.

1. In the Group Policy Management window, expand **Forest: Adatum.com**,expand
    **Domains**, expand **Adatum.com**, and then select **Marketing**.

1. Right-click **Marketing**, and then select **Create a GPO in this domain
    and link it here**. Name the new GPO **Marketing** and select **OK**. Right-click the **Marketing** GPO and select **Edit**.

1. In the Group Policy Management Editor window, expand **Computer
    Configuration**, expand **Policies**, expand **Windows Settings**, expand
    **Security Settings**, expand **Application Control Policies**, expand
    **AppLocker**, and then select **Windows Installer Rules**.

1. Right-click **Windows Installer Rules**, and then select **Create Default
    Rules**.

1. Right-click **Windows Installer Rules**, and then select **Create New Rule**.

1. On the Before You Begin page, select **Next**.

1. On the Permissions page, select **Deny**, and then select **Next**.

1. On the Conditions page, select **Path**, and then select **Next**.

1. On the Path page, select **Browse Files**.

1. In the File name text box, type **\\\\lon-dc1\\labfiles\\apps**, and then
    press **Enter**.

1. In the Open dialog box, double-click **XmlNotepad.msi**, and then select
    **Next**.

1. On the Exceptions page, select **Next**, and then select **Create**.

1. In the navigation pane, right-click **AppLocker**, and then select
    **Properties**.

1. In the AppLocker Properties dialog box, under Windows Installer rules,
    select the **Configured** check box, and then select **OK**.

1. In the navigation pane, select **System Services**, and then double-click
    **Application Identity**.

1. In the Application Identity Properties dialog box, select the **Define this
    policy setting** check box, select **Automatic**, and then select **OK**.

1. **Close** the Group Policy Management Editor window.

1. Close Group Policy Management.

### Task 4: Apply the AppLocker policy

1. In the Server Manager window, select **Tools**, and then select **Active
    Directory Users and Computers**.

1. In Active Directory Users and Computers, expand **Adatum.com**, and then
    select **Computers**.

1. Right-click **LON-CL1**, and then select **Move**.

1. In the Move dialog box, select **Marketing**, and then select **OK**.

1. Switch to **LON-CL1** and restart LON-CL1.

1. Sign in to **LON-CL1** using the following credentials:
    - Username: **Adatum\\Benjamin**
    - Password: **Pa55w.rd**

1. On the desktop, on the taskbar, select the **File Explorer** icon.

1. In the File Explorer address bar, type
    **\\\\lon-dc1\\labfiles\\Apps\\XmlNotepad.msi**, and then press **Enter**.

1. In the Windows Installer dialog box, select **OK**.

1. Sign out of **LON-CL1**.

1. Update the Resolution section of the incident record with the following
    comments:
    - Enabled Default Windows Installer rules.
    - Verified the installer path in the Deny rule.
    - Turned on AppLocker enforcement.
    - Configured policy to start the Application Identity service.
    - Moved a computer, LON-CL1, to Marketing OU to test the policy.

**Results**: After completing this exercise, you should have successfully resolved the AppLocker policy application problem.

## END OF LAB
