# Practice Lab: Configuring BitLocker

## Summary

In this exercise you will learn how to encrypt a local disk drive using BitLocker.

### Scenario

You have a Windows 10 computer that has sensitive data stored on the E drive. You decide to configure and test BitLocker to see how it can be used to protect the data files that are stored on the local drive (E:).

### Task 1: Configure GPO settings

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**.

2. Select the Start menu, type **gpedit.msc**, and then press Enter.

3. In the Local Group Policy Editor, under **Computer Configuration** node, expand **Administrative Templates**, expand **Windows Components**, and then expand **BitLocker Drive Encryption**.

4. Select **Operating System Drives**, and then double-click **Require additional authentication at startup**.

5. In the **Require additional authentication at startup** dialog box, select **Enabled**, and then select **OK**.

6. Close the Local Group Policy Editor.

   *Note: This configuration change is made to enable BitLocker without a TPM. This is a necessary step with virtual machines, but would not be typical on most Windows 10 devices.*

### Task 2: Enable BitLocker

1. On the taskbar, select the **File Explorer** icon.

2. In File Explorer, in the navigation pane, expand **This PC**.

3. In the navigation pane, right-click **Allfiles (E:)**, and then select **Turn on BitLocker**.

4. In the **BitLocker Drive Encryption (E:)** dialog box, select **Use a password to unlock the drive**.

5. In the **Enter your password** and **Reenter your password** boxes, type **Pa55w.rd**, and then select **Next**.

6. On the **How do you want to back up your recovery key?** page, select **Save to a file**.

7. In the **Save BitLocker recovery key as** dialog box, select **Local Disk (C:)**.

8. Select **New folder**, type **BitLocker**, and then press Enter.

9. In the **Save BitLocker recovery key as** dialog box, select **Open**, and then select **Save**,

10. On the **How do you want to back up your recovery key?** page, select **Next**.

11. On the **Choose how much of your drive to encrypt** page, ensure that **Encrypt used disk space only (faster and best for new PCs and drives)** is selected, and then select **Next**.

12. On the **Choose which encryption mode to use** page, ensure that **New encryption mode (best for fixed drives on this device)** is selected, and then select **Next**.

13. On the **BitLocker Drive Encryption (E:)** page, select **Start encrypting**, and then select **Close**. Notice the lock icon next to the Allfiles (E:) node in the navigation bar, which indicates that the drive is currently unlocked.

14. Restart SEA-CL1.

### Task 3: Verify BitLocker

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**.
2. Select the **File Explorer** icon on the taskbar.
3. In File Explorer in the navigation pane expand **This PC**, and select **Local Disk (E:)**. Notice the lock icon next to Local Disk (E:). This indicates that the drive is protected by BitLocker.
4. In the BitLocker (E:) window, enter the password **Pa55w.rd**, press Enter to unlock the drive, and then verify access to the drive contents.
5. Right-click **Allfiles (E:)** and then select **Manage BitLocker**. Take note of the options available for managing BitLocker on Allfiles (E:).
6. Select **Turn off BitLocker**.
7. In the BitLocker Drive Encryption dialog box, select **Turn off BitLocker**.
8. Close the BitLocker Drive Encryption window.
9. In File Explorer, notice that that lock icon is no longer visible next to Allfiles (E:).
10. Close all open windows and sign out of SEA-CL1.

**Results**: After completing this exercise, you will have configured BitLocker to encrypt a local disk drive.

**END OF LAB**