# Practice Lab: Remote Management 

## Summary

In this lab you will learn how to mange windows devices remotely.

### Scenario

Your company is planning to open a new branch office. To manage the devices in the new branch office you need to use Remote PowerShell and Remote Desktop. You want to test the functions upfront by running some remote PowerShell commands on LON-CL1. Then you disable PowerShell Remoting to see what's happening. Lastly you enable Remote Desktop on LON-CL1 as a fallback solution.

### Task 1: Test PowerShell Remoting

1. Sign in to **LON-CL2** as **adatum\\Administrator** with the password: **Pa55w.rd**.

1. Right-click **Start**, and then select **Windows PowerShell**.

1. In the Windows PowerShell window, type the following command, and then press **Enter**:

    ```powershell
    Get-Service -ComputerName LON-CL1 | Where-Object {$_.Status -eq "Stopped"}
    ```

1. In the Windows PowerShell window, type the following command, and then press **Enter**:

    ```powershell
    Set-Service -ComputerName LON-CL1 -Name WlanSvc -Status Running
    ```

1. In the Windows PowerShell window, type the following command, and then press **Enter**:

    ```powershell
    Invoke-Command -ComputerName LON-CL1 -ScriptBlock {Get-ChildItem "C:\Program Files"}
    ```

1. In the Windows PowerShell window, type the following command, and then press **Enter**:

    ```powershell
    Test-WsMan LON-CL1
    ```

1. In the Windows PowerShell window, type the following commands, and then press **Enter**:

    ```powershell
    Enter-PSSession LON-CL1
    Add-Content Remote.txt "Adding text to file on LON-CL1"
    Exit-PSSession
    ```

### Task 2: Disable PowerShell Remoting

1. Switch to **LON-CL1**.

1. Sign in to **LON-CL1** as **adatum\\Administrator** with the password: **Pa55w.rd**.

1. Right-click **Start**, and then select **Windows PowerShell (Admin)**.

1. In the Administrator: Windows PowerShell window, type the following command, and then press **Enter**:

    ```powershell
    Disable-PSRemoting -Force
    ```

1. Select the **File Explorer** icon on the taskbar, browse to **Documents** and double-click **remote.txt**.

1. Close all open windows.

1. Switch to **LON-CL2**

1. In the Windows PowerShell window, type the following command, and then press **Enter**:

    ```powershell
    Invoke-Command -ComputerName LON-CL1 -ScriptBlock {Get-ChildItem "C:\Program Files"}
    ```

    _Note: The command is failing now._

1. Close all open windows.

### Task 3: Enable Remote Desktop

1. Switch to **LON-CL1**.

1. Select **Start**, and then Select the **Settings** icon.

1. In **Settings**, select **System**.

1. On the **System** tab, select **Remote Desktop**.

1. Switch **Enable Remote Desktop** on.

1. In the Remote Desktop Settings window select **Confirm**.

1. Close the **Settings** app.

**Results**: After completing this exercise, you will have enabled and tested the remote management functions of windows.

## END OF LAB
