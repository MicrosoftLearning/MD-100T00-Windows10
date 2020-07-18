# Practice Lab: Configuring and Managing Hyper-V

## Summary

In this lab you will learn how to create a virtual machine in Hyper-V and modify
its settings using PowerShell.

### Scenario

To test a new application you need to setup a virtual machine on your Hyper-V
server LON-HOST1 and modify its settings to fit to the requirements of the
application. Before you install the application you test if you can revert the
VM to an checkpoint as a backup solution in case the install fails.

### Task 1: Creating a virtual machine in Hyper-V

1. Sign in to **LON-HOST1** as **ADATUM\\Administrator** with the password
    **Pa55w.rd.**

1. In the taskbar select the **Hyper-V Manager** icon.

1. In the Hyper-V Manager window select **New**, and then select **Virtual
    Machine**.

1. In the New Virtual Machine Wizard window select **Next**, then enter
    **LON-TEST** in the Name field and select **Next**.

1. Select **Generation 1** and select **Next**. Leave the default startup
    memory and select **Next**.  
    In the Connection list select **External network**, and select Next.

1. In the Size box enter **75**, and select **Next.**

1. On the Installation Options page, leave the default to install the operating
    system later, and select **Next** then select **Finish**.

### Task 2: Add an ISO file to a VM

1. In Hyper-V Manager, select **LON-TEST**.

1. In the Actions pane, select **Settings**.

1. In the Settings window select **IDE Controller 1** on the left.

1. Select **DVD Drive** and then select **Add**.

1. In the Location drop-down, select a location number not already in use.

1. In the Media area, select the **Image file** option, and select **Browse**.

1. Browse to **C:\\Labfiles**, select **Windows.iso** and select **Open**.

1. Select **OK** to close the Settings window.

1. Right-click on **LON-TEST** and select **Start**.

### Task 3: Managing virtual machine settings with PowerShell

1. Right-click **Start** and select **Windows Powershell (Admin)**.

1. At the PowerShell window, type the following command and then press
    **Enter**:

   ```powershell
   Get-VM LON-Test | Set-VMMemory -StartUpBytes 2GB
   ```

1. Confirm that for LON-Test the StartUpBytes is now set to 2GB.

1. At the PowerShell window, type the following command and then press
    **Enter**:

   ```powershell
   Get-VM LON-Test | Add-VMNetworkAdapter -SwitchName "External Network"
   ```

1. Confirm that LON-Test has now an additional network adapter that is
    connected to the virtual switch "External Network".

1. Close the PowerShell window.

### Task 4: Creating a snapshot

1. Switch to the Hyper-V Manager window.

1. In the Virtual machine area select **LON-CL5** and then select **Settings.**

1. In the navigation area select **Network Adapter.**

1. In the Network Adapter settings, in the Virtual switch drop-down select
    "**Not connected**", and then select **OK**.

    _Note: This is done to prevent Windows from updating, which would
    lengthen the time of the lab._

1. In the Virtual machine area select **LON-CL5** and then select
    **Checkpoint.**

    _Note: Creation of the checkpoint may take a couple of minutes._

1. Once the snapshot is created select **OK**. In the checkpoint area you can now see the snapshot.

1. Select **Connect.**

1. On **LON-CL5** inside the Virtual Machine Connection Window in the taskbar
    select the **File Explorer** icon.

1. Navigate to the **C:\\Users\\Student** folder. Right-click the **Documents**
    folder, and then select **Delete**.

1. Close the Virtual Machine Connection window.

1. Select **Revert.**

1. In the Revert Virtual Machine Window select **Revert.**

1. Select **Start.**

1. Select **Connect.**

1. On **LON-CL5** inside the Virtual Machine Connection Window verify that the
    **Documents** folder is available again.

1. Close all open windows.

**Results:** After finishing the exercise you have created a Hyper-V virtual
machine and managed its settings.

## END OF LAB
