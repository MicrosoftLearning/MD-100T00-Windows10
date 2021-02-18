# Practice Lab: Managing password and account options

## Summary

In this lab you will learn how to create and manage domain password policies, account options, and User Account Control.

## Exercise 1: Managing Domain Password Policies

### Scenario

You have been delegated the task to configure the domain password policy for Contoso.com. Part of your task is to implement a new security requirement that specifies a longer password and a 20 minute account lockout if a user incorrectly enters their password more than twice in succession.

*Note: You will use SEA-SVR1 which includes all Windows Administrative Tools for remotely managing SEA-DC1 and to perform Active Directory management tasks.*

### Task 1: Configure password and account options

1. Sign in in to SEA-SVR1 as **Contoso\\Administrator**  with the password **Pa55w.rd**.
2. Click **Start** and then select **Server Manager**.
3. Select **Tools** and then select **Group Policy Management.**
4. In the Group Policy Management console, expand **Forest:Contoso.com\\Domains\\Contoso.com**, and then select the **Group Policy Objects** node.
5. In the **Group Policy Objects in Contoso.com** window, right‑click the **Default Domain Policy** policy, and then select **Edit**.
6. In the Group Policy Management Editor, expand the **Computer Configuration\\Policies\\Windows Settings\\Security Settings\\Account Policies** node, and then select **Password Policy.**
7. In the list of policies, double-click the **Minimum password length** policy.
8. On the **Minimum password length Properties** page, set the **Password must be at least** value to **12** characters, and then select **OK**.
9. In the console tree, select the **Account Lockout Policy** node.
10. Double-click the **Account lockout duration** policy.
11. In the **Account Lockout Duration Properties** dialog box, select **Define this policy setting**, and then set the **Account is locked out for** value to **20** minutes. Select **OK**.
12. In the **Suggested Value Changes** dialog box, select **OK**.
13. Double-click the **Account lockout threshold** policy.
14. In the **Account lockout threshold Properties** dialog box, set the **Account will lock out after** setting to **2** invalid logon attempts, and then select **OK**.
15. Close the Group Policy Management Editor.
16. Close the Group Policy Management console.
17. In Server Manager, in the **Tools** list, select **Active Directory Users and Computers**.
18. Expand the **Contoso.com** node, and then select the **IT** OU.
19. Right-click the **Jane Dow** user account, and then select **Properties**.
20. In the **Jane Dow Properties** dialog box, select the **Account** tab.
21. In the list of **Account Options**, clear the **Password never expires** check box, and then select the **User must change password at next logon** check box. select **OK**.

### Task 2: Refresh GPOs

1. On LON-DC1, right-click **Start**, and then select **Windows PowerShell (Admin)**.

2. In the Administrator: Windows PowerShell window, type the following command, and then press **Enter**:

    ```powershell
    Invoke-Gpupdate -force
    ```

3. Close the **Active Directory Users and Computers** and the **Windows PowerShell** window.

**Results**: After completing this exercise you created a password policy that will affect the password settings for all domain users.

## Exercise 2: Testing Password Policy Settings

### Scenario

After configuring a more strict set of password policies you will then ask Jane Dow to test the policy settings.

### Task 1: Verify password settings

1. Switch to **SEA-CL1** and sign in as **Contoso\\Jane** with the password **Pa55w.rd**.

2. When the message appears that indicates the user’s password must be changed before signing in, select **OK**.

3. In the New password box and the Confirm password box, type **Pa55w.rd12**, and then press **Enter**.

4. When the message displays that indicates that the new password does not meet the length, complexity, or history requirements of the domain, select **OK**. Type the old password, **Pa55w.rd**.

5. In the New password box and the Confirm password box, type **Pa55w.rd1234**, and then press **Enter**.

6. When a message displays that indicates that the password has been changed, select **OK**.

7. Sign out of **SEA-CL1**.

### Task 2: Attempt repeated sign-ins

1. Attempt to sign in to **SEA-CL1** as **Contoso\\Jane** with the incorrect password **password1**.

2. When a message displays that indicates that the password is incorrect, select **OK**.

3. Attempt again to sign in to **SEA-CL1** as **Contoso\\Jane** with the incorrect password **password1**.

4. When a message displays that indicates that the password is incorrect, select **OK**.

5. Attempt again to sign in to **SEA-CL1** as **Contoso\\Jane** with the incorrect password **password1**.

6. When the message displays that indicates that the referenced account is locked out, select **OK**.

### Task 3: Unlock a locked account

1. Sign in in to SEA-SVR1 as **Contoso\\Administrator**  with the password **Pa55w.rd**.
2. Click **Start** and then select **Server Manager**.
3. In Server Manager, in the **Tools** list, select **Active Directory Users and Computers**.
4. Expand the **Contoso.com** node, and then select the **IT** OU.
5. Right-click the **Jane Dow** user account, and then select **Properties**.
6. In the **Jane Dow Properties** dialog box, select the **Account** tab.
7. Select the check box next to **Unlock account**. **This account is currently locked out on this Active Directory Domain Controller**.
8. Select **OK** to close the **Jane Dow Properties** box.
9. Close **Active Directory Users and Computers**.

**Results**: After completing this exercise you verified that the password policy works as expected.

## Exercise 3: Configuring UAC

### Scenario

You need to configure UAC so that when the UAC dialog box prompts a standard user, he or she can enter the credentials of an administrator account to gain elevated privileges. You also need to restrict the execution of unsigned applications.

### Task 1: Modify UAC prompts

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**.

2. In the **Type here to search** box on the taskbar, type **gpedit.msc**, and then press Enter.

3. In the Local Group Policy Editor, expand **Computer Configuration**, expand **Windows Settings**, expand **Security Settings**, expand **Local Policies**, and then select **Security Options**.

4. In the results pane, double-click **User Account Control: Behavior of the elevation prompt for standard users**.

5. In the **User Account Control: Behavior of the elevation prompt for standard users** dialog box, select the **Prompt for credentials** drop down list, select **Prompt for credentials on the secure desktop**, and then select **OK**.

6. In the results pane, double-click **User Account Control: Only elevate executables that are signed and validated**.

7. In the **User Account Control: Only elevate executables that are signed and validated** dialog box, select **Enabled**, and then select **OK**.

8. In the results pane, double-click **User Account Control: Behavior of the elevation prompt for administrators in Admin Approval Mode**.

9. In the **User Account Control: Behavior of the elevation prompt for administrators in Admin Approval Mode** dialog box, select the **Prompt for consent for non-Windows binaries** drop down list, select **Prompt for consent on the secure desktop**, and then select **OK**.

10. Close the Local Group Policy Editor.

11. Sign out of **SEA-CL1**.

### Task 2: Test the UAC prompts as a standard user

1. Sign in to **SEA-CL1** as **Contoso\\Jon** with the password **Pa55w.rd**.

2. Right-click **Start**, and then select **Windows PowerShell (Admin)**.

   _**Note**: The Windows operating system displays the User Account Control prompt._

3. In the **User name** box, type **Administrator**, and in the **Password** box, type **Pa55w.rd**, and then select **Yes**.

4. Close the Windows PowerShell prompt.

5. Sign out of **SEA-CL1**.

### Task 3: Verify the UAC notifications as an administrator

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**.

2. In the **Type here to search** box on the taskbar, type **Control Panel**, and then press Enter.

3. In Control Panel, select **System and Security**.

4. In **System and Maintenance**, select **Change User Account Control settings**.

5. Verify that the slider is configured for **Always notify**.

6. Select **Cancel**.

7. Close all open windows and sign out of SEA-CL1.

**Results**: After completing this exercise you have configured the prompt behavior of UAC.

**END OF LAB**