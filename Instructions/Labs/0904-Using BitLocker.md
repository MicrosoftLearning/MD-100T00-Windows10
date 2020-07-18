# Practice Lab: Using BitLocker

## Summary

In this exercise you will learn how to encrypt a local drive using BitLocker.

### Scenario

Adatum engineering department has a Windows 10 computer that has sensitive data
store on the E drive. Engineering needs access to this data, but IT has concerns
about the location's security and concerns with equipment theft. You have
decided to implement BitLocker to protect the user’s data files that are stored
on the local drive (E:).

 

### Task 1: Configure GPO settings

1.  Sign in to **LON-CL1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

2.  In the T**ype here to search box** on the taskbar, type **gpedit.msc**, and
    then press Enter.

3.  In the Local Group Policy Editor, under **Computer Configuration** node,
    expand **Administrative Templates**, expand **Windows Components**, and then
    expand **BitLocker Drive Encryption**.

4.  Select **Operating System Drives**, and then double-click **Require
    additional authentication at startup**.

5.  In the **Require additional authentication at startup** dialog box, select
    **Enabled**, and then select **OK**.

6.  Close all open windows.



### Task 2: Enable BitLocker

1.  Select the **File Explorer** icon on the taskbar.

2.  In File Explorer, in the navigation pane, expand **This PC**.

3.  In the navigation pane, right-click Allfiles (E:), and then select **Turn on
    BitLocker**.

4.  In the **BitLocker Drive Encryption (E:)** dialog box, select **Use a
    password to unlock the drive**.

5.  In the **Enter your password** and **Reenter your password** boxes, type
    **Pa55w.rd**, and then select **Next**.

6.  On the **How do you want to back up your recovery key?** page, select **Save
    to a file**.

7.  In the **Save BitLocker recovery key as** dialog box, select **Local Disk
    (C:)**.

8.  Select **New folder**, type **BitLocker**, and then press Enter.

9.  In the **Save BitLocker recovery key as** dialog box, select **Open**, and
    then select **Save**,

10. On the **How do you want to back up your recovery key?** page, select
    **Next**.

11. On the **Choose how much of your drive to encrypt** page, ensure that
    **Encrypt used disk space only (faster and best for new PCs and drives)** is
    selected, and then select **Next**.

12. On the **Choose which encryption mode to use** page, ensure that **New
    encryption mode (best for fixed drives on this device)** is selected, and
    then select **Next**.

13. On the **BitLocker Drive Encryption (E:)** page, select **Start
    encrypting**, and then select **Close**.

14. Wait until the drive is fully encrypted. The progress is shown by the
    BitLocker icon in the notification area

15. Restart LON-CL1.



### Task 3: Verify BitLocker

1.  Sign in to **LON-CL1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

2.  Select the **File Explorer** icon on the taskbar.

3.  In File Explorer in the navigation pane expand **This PC**, and select
    **Local Disk (E:)**.

4.  In the BitLocker (E:) window, enter the password **Pa55w.rd**, press Enter
    to unlock the drive, and then verify access to the drive contents.  
    *Note: In the rest of this lab in this module, you must always enter the
    password to unlock the E: drive after a reboot.*

5.  Close all open windows.


**Results**: After completing this exercise, you should have configured
BitLocker to encrypt a local drive.

**END OF LAB**