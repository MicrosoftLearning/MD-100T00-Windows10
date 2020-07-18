# Practice Lab: Enabling Disk Quotas

## Summary

To prevent specific users from using to much disk space disk quota can be
established.

### Scenario

You discover that some of your colleagues are using a high amount of disk
storage on the E: drive of LON-CL1. This is preventing other users from saving
their files. You decide to create disk quotas of 500 MB with a warning set at
250 MB, and ask Ada Russell to test if the configuration is correct.

### Task 1: Create disk quotas

1. Sign in to **LON-CL1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

1. Select the **File Explorer** icon on the taskbar.

1. In the File Explorer window, right-click **Allfiles (E:)**, and then select
    **Properties**.

1. Select the **Quota tab**, and then select **Show Quota Settings**

1. In the Quota Settings for Allfiles (E:) window select the **Enable quota
    management** check box and select the **Deny disk space to users exceeding
    quota limit** check box.

1. Select **Limit disk space to**, in the Limit disk space to text box, type **500**, and then in the Set warning level to text box, type **250**.

1. Select **MB** as the unit for both values.

1. In the Properties window, select **OK**, and then in the Disk Quota window,
    select **OK**.

1. Right-click **Start**, select **Shut down or sign out**, and then select
    **Restart**.

1. Note that LON-CL1 will restart now

### Task 2: Create test files

1. Sign in as the user **Adatum\\ada** with the password **Pa55w.rd.**

1. Select **Start**, and then type **cmd**. Press **Enter**.

1. At the command prompt type the following five commands:

   ```bat
   E:

   MKDIR research

   CD research

   Fsutil file createnew file1.txt 209715200

   Fsutil file createnew file2.txt 209715200

   ```

1. Sign out.

### Task 3: Verify the disk quota functionality

1. Sign in as **Adatum\\Administrator** with the password **Pa55w.rd**.

1. Select the **File Explorer** icon on the taskbar.

1. In the File Explorer window, right-click **Allfiles (E:),** and then select
    **Properties**.

1. Select the **Quota tab**, and then select **Show Quota Settings.**

1. In the Quota Settings for Allfiles (E:) window select **Quota Entries**.

1. Notice the warning for Ada Russell for the disk space used. You might need
    to expand some columns to read the full name and Logon Name.

1. Close the **Quota Entries** for Data (E:) window.

1. Click **OK** to close the Data (E:) Properties window.

1. Close all open windows

**Results**: After completing this exercise, you will have configured disk
quotas.

## END OF LAB
