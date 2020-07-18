# Practice Lab: Creating a Storage Space

## Summary

In this lab you will configure a storage space that will combine multiple hard
disks to one big single disk.

### Scenario

The sales department requires a new file share that need to use a mirror for
resilience. You decide to reuse the three hard disks you have already added to
LON-CL3 and configure a storage space. You have to remove the partition from the
already used disk first and then create a two-way mirror storage pool inside a
newly created storage space.

 

### Task 1: Initialize the required disks

1.  Sign in to **LON-CL3** as **LON-CL3\\Admin** with the password **Pa55w.rd**.

2.  Right-click **Start**, and then select **Windows PowerShell (Admin)**.

3.  At the PowerShell Window type the following command and confirm with "Yes":

```
Clear-Disk -Number 1 -RemoveData
```

4.  At the PowerShell Window type the following command and confirm with "Yes":

```
Get-Disk \| Where partitionstyle -eq 'raw' \| Initialize-Disk -PartitionStyle MBR
```

### Task 2: Create a mirrored storage pool

1.  Select **Start**, and then type **Storage**. Select **Manage Storage Spaces** in the list.

2.  Select **Create a new pool and storage space**.

3.  In the **Create a storage pool** window notice that Disk 1, Disk 2, and Disk
    3 are selected. Select **Create pool**.

4.  In the **Drive letter** dropdown field select E:

5.  Notice that a resilience type of Two-way mirror is selected.

6.  Click **Create storage space**. This will automatically open the File
    Explorer window.

 

### Task 3: Verify that the volume is available in File Explorer 

1.  In File Explorer, right-click **Storage Space (E:)**, and then Select
    **Properties**.

2.  Notice that the capacity is approximately 187 gigabytes (GB).

3.  Close all open windows

 

**Results**: After completing this exercise, you will have created a two-way
mirror storage space.

**END OF LAB**