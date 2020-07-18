# Practice Lab: Migrating User Settings using USMT

## Summary

In this lab you will learn how to migrate user settings from one computer to another using the User State Migration Tool (USMT).

### Scenario

You have to replace the computer of one of your colleagues. He requires you to copy his user settings from the old computer, LON-CL2, to the new computer, LON-CL1. The best way to do so is using the User State Migration Tool (USMT). The USMT install files are located at \\\\LON-DC1\\Labfiles\\USMT. A location to store migration data has been provided at \\\\LON-DC1\\Labfiles\\Install\\MigrationStore.

### Task 1: Prepare the source computer 

1. Sign in to **LON-CL2** as **ADATUM\\administrator**, Password: **Pa55w.rd**

1. Right-click the **desktop**, hover over the **New** menu item, and then select **Text Document**. Type **Demofile** and press **Enter**.

1. Double-click **Demofile.txt** and type some random text. Press **Alt+F4**, and then select the **Save** button.

1. Select **Start** and type **cmd**. Select **Run as administrator**. In the **User Account Control** window select **Yes**

1. At the command prompt, type the following command, and then press **Enter**:

   ```cmd
   Net Use F: \\LON-DC1\Labfiles\Install\USMT
   ```

1. At the command prompt, type **F:**, and then press **Enter**.

1. At the command prompt, type the following, and then press **Enter**:

   ```cmd
   Scanstate \\LON-DC1\Labfiles\Install\MigrationStore\LON-CL2 /i:migapp.xml /i:miguser.xml /o
   ```

_**Note**: This will take several minutes to complete._

1. Close all open windows.

### Task 2: Complete the migration

1. Switch to **LON-CL1**
1. Sign in to **LON-CL1** as **Adatum\\Administrator** with the password **Pa55w.rd**

- *Notice that there is no Demofile.txt on the desktop and no OneNote icon in the taskbar.*

1. Select **Start** and type **cmd**. Select **Run as administrator**. In the **User Account Control** window select **Yes**

1. At the command prompt, type the following command, and then press **Enter**:

   ```cmd
   Net Use F: \\LON-DC1\Labfiles\Install\USMT
   ```

1. At the command prompt, type **F:**, and then press **Enter**.

1. At the command prompt, type the following, and then press **Enter**:

   ```cmd
   loadstate \\LON-DC1\Labfiles\Install\MigrationStore\LON-CL2 /i:migapp.xml /i:miguser.xml /lac:Pa55w.rd /lae
   ```

_**Note**: This will take several minutes to complete._

1. Type **exit** to close the command prompt.

1. Sign out.

1. Sign in to LON-CL1 as **Adatum\\Administrator** with the password
    **Pa55w.rd**

_**Notice** that the demofile.txt is now on the desktop and the OneNote icon is visible on the taskbar._

### END OF LAB
