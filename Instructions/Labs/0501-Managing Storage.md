# Practice Lab: Managing Storage 

## Summary

In this lab you will learn how to manage disk using Disk Management and PowerShell.

## Exercise 1: Creating a Simple Volume 

### Scenario
LON-CL3 needs to be able to store video on an additional hard drive. Additional disks have been installed, but disk 1 needs to be configured as the E: drive for 5120 KB. 


### Task 1: Use Disk Management to initialize a disk
1.  Sign in to LON-CL3 as **LON-CL3\\Admin** with the password **Pa55w.rd**

2.  Right-click Start and select **Disk Management**.

3.  In the Initialize Disk window, **clear the Disk 2 and Disk 3** check boxes,
    and then select **OK**. You can see that Disk 1 now has a status of Online.

### Task 2: Create a simple volume
1.  Right-click the right side of Disk 1, and then select **New Simple Volume**.

2.  In the New Simple Volume Wizard window, select **Next**.

3.  On the Specify Volume Size page, **type 5120**, and then select **Next**.

4.  On the Assign Drive Letter or Path page, make sure that **Assign the following drive letter: E** is selected, and then select **Next**.

5.  On the Format partition page, in the Volume Label text box, type **Data**, and then select **Next**.

6.  On the Completing the New Simple Volume Wizard page, select **Finish**. If you receive the error message Location is not available, then select OK.

    _Note: If prompted whether to format drive E:, select Cancel._

7.  Close the **File Explorer** window.

**Results:** After completing this exercise, you will have initialized one hard disk.

## Exercise 2: Creating a Simple Volume

### Scenario
The initial storage expectations needed for video on LON-CL3 was incorrect. Your manager has asked you to use PowerShell to configure the E drive to use the entire disk. 

### Task 2: Extend the simple volume
1.  Right-click Start, and then select **Windows PowerShell (Admin)**.

2.  In Windows PowerShell, type the following two commands:
```
$MaxSize = (Get-PartitionSupportedSize -DriveLetter e).sizeMax
Resize-Partition -DriveLetter e -Size $MaxSize
```  

3.  Switch to the **Disk Management window**, and then verify that the E volume now occupies the entire Disk 1.  

    _Note: If the change is not visible, press F5 to refresh the view in Disk Management._

4.  **Close** all open Windows.

**Results**: After completing this exercise, you will have created a simple volume and then extended the volume.

**END OF LAB**