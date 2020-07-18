# Practice Lab: Creating Security Policies
 

## Summary
In this lab you will learn how to create and modify Security Policies.


## Exercise 1: Creating Security Policies


### Scenario

You are concerned about the security of your organization’s user-account
passwords. Therefore, you want to implement a more strict set of password
policies in your active directory forest, which require longer passwords and
account lockouts if users incorrectly enter their password more than twice in
succession.



### Task 1: Configure password and account options

1.  Sign in in to **LON-DC1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

2.  On **LON-DC1**, in Server **Manager**, in the Tools list, select **Group Policy Management.**

3.  In the Group Policy Management Console, expand
    **Forest:Adatum.com\\Domains\\Adatum.com**, and then select the **Group
    Policy Objects** node.

4.  In the Group Policy Objects in Adatum.com window, right‑click the **Default
    Domain Policy** policy, and then select **Edit**.

5.  In the Group Policy Management Editor, expand the **Computer
    Configuration\\Policies\\Windows Settings\\Security Settings\\Account
    Policies** node, and then select **Password Policy.**

6.  In the list of policies, double-click the **Minimum password length**
    policy.

7.  On the **Minimum password length Properties** page, set the **Password must
    be at least** value to **12** characters, and then select **OK**.

8.  In the console tree, select the **Account Lockout Policy** node.

9.  Double-click the **Account lockout duration** policy.

10. In the **Account Lockout Duration Properties** dialog box, select **Define
    This Policy Setting**, and then set the **Account Is Locked Out For** value
    to **20** minutes. Select **OK**.

11. In the **Suggested Value Changes** dialog box, select **OK**.

12. Double-click the **Account lockout threshold** policy.

13. In the **Account Lockout Threshold Properties** dialog box, set the
    **Account Will Lock Out After** settings to **2** invalid logon attempts,
    and then select **OK**.

14. Close the Group Policy Management Editor.

15. Close the Group Policy Management Console.

16. In Server Manager, in the Tools list, select **Active Directory Users and
    Computers**.

17. Expand the **Adatum.com** node, and then select the **IT** OU.

18. Right-click the **Abbi Skinner** user account, and then select
    **Properties**.

19. In the **Abbi Skinner Properties** dialog box, select the **Account** tab.

20. In the list of **Account Options**, clear the **Password never expires**
    check box, and then select the **User must change password at next logon**
    check box. select **OK**.



### Task 2: Refresh GPOs

1.  On LON-DC1, right-click **Start**, and then select **Windows PowerShell
    (Admin)**.

2.  In the Administrator: Windows PowerShell window, type the following command,
    and then press **Enter**:

    ```
    Invoke-Gpupdate -force
    ```

3.  Close the Active Directory Users and Computers and PowerShell window


## Exercise 2: Testing Security Policies

### Scenario

After configuring a more strict set of password policies you will then ask Abbi
Skinner to test the policies.

### Task 1: Change your password

1.  Switch to **LON-CL1.**     

2.  Sign in to **LON-CL1** as **Adatum\\Abbi** with the password **Pa55w.rd**.

3.  When the message appears that indicates the user’s password has expired and
    must be changed before signing in, select **OK**.

4.  In the New Password box and the Confirm Password box, type **Pa55w.rd12**,
    and then press **Enter**.

5.  When the message displays that indicates that the new password does not meet
    the length, complexity, or history requirements of the domain, select
    **OK**. Type the old password, **Pa55w.rd**.

6.  In the New Password box and the Confirm Password box, type **Pa55w.rd1234**,
    and then press **Enter**.

7.  When a message displays that indicates that the password has been changed,
    select **OK**.

8.  After signing in, right-click **Start**, and then select **Windows
    PowerShell**.

9.  At the Windows PowerShell prompt, type the following command, and then press
    **Enter**:

    ```
    gpupdate /force
    ```

1.  Sign out of **LON-CL1**.

### Task 2: Attempt repeated sign-ins

1.  Attempt to sign in to **LON-CL1** as **Adatum\\Abbi** with the incorrect
    password **Potato**.

2.  When a message displays that indicates that the password is incorrect,
    select **OK**.

3.  Attempt again to sign in to **LON-CL1** as **Adatum\\Abbi** with the
    incorrect password **Potato**.

4.  When a message displays that indicates that the password is incorrect,
    select **OK**.

5.  Attempt again to sign in to **LON-CL1** as **Adatum\\Abbi** with the
    incorrect password **Potato**.

6.  When the message displays that indicates that the referenced account is
    locked, and you may not sign in, select **OK**


**Results**: After completing this exercise you created a Security Policy that
will affect the password settings for all domain users.

**END OF LAB**