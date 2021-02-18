# Practice Lab: Recovering Windows by using a Restore Point

## Summary

During this lab, you will learn how to recover a Windows 10 device by using a Restore Point.

### Scenario

One your colleagues reports that after installing a hardware driver that his device is no longer responsive. You've decided to see if you can reproduce the same circumstances on SEA-CL1, but need to ensure that you can return to a previous working state. 

### Lab Preparation

To complete this lab you need to attach **Win10_20H2_Eval.iso** to SEA-CL1. Consult with your instructor on how to perform this task.

### Task 1: Configure System Protection and Create a System Restore Point

1.  Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password of **Pa55w.rd**.
    
2. On the taskbar, select **File Explorer**.

3. In File Explorer, in the navigation pane, right-click **This PC**, and then select **Properties**.

4. On the About page, scroll down and then select **System protection**.

5. In the **System Properties** dialog box, in the **Protection Settings** section, select **Local Disk (C:) (System)**, select **Configure**, select **Turn on system protection**, move the **Max Usage** slider to **5%**, and then select **OK** twice.

6. Right-click **Start** and select **Windows PowerShell (Admin).**

7. In the Administrator: PowerShell window type the following command and press **Enter**:

   ``` 
   Checkpoint-Computer -Description "Lab Start"
   ```

8.  When complete, close the PowerShell Window. 

### Task 2: Simulate the Problem

1.  On SEA-CL1, in File Explorer, browse to **E:\\Labfiles\Mod13**.
2.  In the Mod13 folder, double-click **scenario1.vbs**. SEA-CL1 will restart.
3.  After the computer restarts, a blue screen displays that states that the device ran into a problem. Take note of the Stop code that states INACCESSIBLE BOOT DEVICE. 

### Task 3: Perform a System Restore

1.  Restart SEA-CL1. 
2.  When prompted to **Press any key to boot from CD or DVD**, select the spacebar. The computer starts into Windows Setup.
3.  In Windows Setup, select **Next**.
4.  On the **Install now** page, select **Repair your computer**.
5.  On the **Choose an option** page, select **Troubleshoot**.
6.  On the **Advanced options** page, notice the five tools that are available. 
7.  On the Advanced options page, highlight **System Restore** and press **Enter**.
8.  On the Choose a target operating system page, select **Windows 10**.
9.  On the Restore system files and settings page, select **Next**.
10.  On the System Restore window, select the **Lab Start** line and select **Scan for affected programs**.
11.  Note that no programs will be affected. Select **Close**.
12.  Select **Next**, then **Finish**, and then **Yes**.
13.  After the restore is complete, select **Restart**. You may be asked to restart twice to complete the restore.
14.  Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password of **Pa55w.rd**.
15.  In the System Restore window select **Close**. 
16.  Sign out of SEA-CL1.

**Results**: After completing this exercise, you should have successfully recovered a Windows 10 device using a System Restore Point.

**END OF LAB**