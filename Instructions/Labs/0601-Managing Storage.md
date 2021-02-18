# Practice Lab: Managing Storage

## Summary

In this lab you will learn how to manage local disk storage using Disk Management and PowerShell.

## Exercise 1: Creating and Managing a Simple Volume

### Scenario

You need to add storage to SEA-WS2. Additional disks have been installed and you now have to create two new partitions to store data.

### Task 1: Use Disk Management to initialize a disk

1. Sign in to SEA-WS2 as **Admin** with the password **Pa55w.rd**.

2. Right-click Start and select **Disk Management**.

3. In the **Initialize Disk** window, remove the check marks next to **Disk 2** and **Disk 3**, and then select **OK**.  Disk 1 now has a status of Online.

### Task 2: Create a simple volume using Disk Management

1. Right-click the Unallocated space on Disk 1, and then select **New Simple Volume**.

2. In the New Simple Volume Wizard window, select **Next**.

3. On the Specify Volume Size page, next to Simple volume size in MB, type **5120**, and then select **Next**.

4. On the Assign Drive Letter or Path page, make sure that **Assign the following drive letter: E** is selected, and then select **Next**.

5. On the Format partition page, in the Volume Label text box, type **Data**.

6. Ensure that the check box is selected next to **Perform a quick format**, and then select **Next**.

7. On the Completing the New Simple Volume Wizard page, select **Finish**. If you receive the error message Location is not available, then select OK.

   _Note: If prompted to format drive E:, select Cancel._

8. From the taskbar, select **File Explorer**. Verify that you have a new E drive named Data.

9. Close the **File Explorer** window.

### Task 3: Create a simple volume using PowerShell

1. Right-click Start and then select **Windows PowerShell (Admin)**.

2. At the command prompt, type the following and then press Enter:

    ```powershell
    New-Partition -DiskNumber 1 -Size 5gb -AssignDriveLetter
    ```

3. At the Microsoft Windows prompt, select **Format disk**.
4. In the Format Local Disk (F:) dialog box, select **Start** and then **OK**.
5. Select **OK** to close the Format Complete message.
6. In the Format Local Disk (F:) dialog box, select **Close**.
7. In **File Explorer**, verify that you have a new F drive named Local Disk.
8. Close the **File Explorer** window. If a Microsoft Windows prompt is visible select **Cancel**.
9. Switch to Disk Management and verify that Drive F shows 5GB in size.

### Task 4: Extend a simple volume

1. In Disk Management, right-click **Data (E:)**, and then select **Extend Volume**.
2. In the Extend Volume Wizard window, select **Next**.
3. On the Select Disks page, next to Select the amount of space in MB, type **8192**, and then select **Next**.
4. On the Completing the Extend Volume Wizard page, select **Finish**. Notice that Drive E is now 13 GB in size.

### Task 5: Shrink a simple volume

1. In Disk Management, right-click **(F:)**, and then select **Shrink Volume**.
2. On the Shrink F: page, next to Select the amount of space to shrink in MB, type **2048**, and then select **Shrink**. Notice that Drive F is now 3 GB in size.
3. Close all open windows and sign out of SEA-WS2.

**Results:** After completing this exercise, you will have managed local disk storage using Disk Management and Windows PowerShell.

**END OF LAB**