# Practice Lab: Remote Management 

## Summary

In this lab you will learn how to mange windows devices remotely.

### Scenario
Your company is planning to open a new branch office. To manage the devices in the new branch office you need to use Remote PowerShell and Remote Desktop. You want to test the functions upfront by running some remote PowerShell commands on LON-CL1. Then you disable PowerShell Remoting to see what's happening. Lastly you enable Remote Desktop on LON-CL1 as a fallback solution.

### Task 1: Test PowerShell Remoting

1.  Sign in to **LON-CL2** as **adatum\\Administrator** with the password: **Pa55w.rd**.

2.  Right-click **Start**, and then select **Windows PowerShell**.

3.  In the Windows PowerShell window, type the following command, and then press **Enter**:

    ```
    Get-Service -ComputerName LON-CL1 | Where-Object {$_.Status -eq "Stopped"}
    ```

4.  In the Windows PowerShell window, type the following command, and then press **Enter**:

    ```
    Set-Service -ComputerName LON-CL1 -Name WlanSvc -Status Running
    ```

5.  In the Windows PowerShell window, type the following command, and then press **Enter**:

    ```
    Invoke-Command -ComputerName LON-CL1 -ScriptBlock {Get-ChildItem "C:\Program Files"}
    ```

6.  In the Windows PowerShell window, type the following command, and then press **Enter**:

    ```
    Test-WsMan LON-CL1
    ```

7.  In the Windows PowerShell window, type the following commands, and then press **Enter**:

    ```
    Enter-PSSession LON-CL1
    Add-Content Remote.txt "Adding text to file on LON-CL1"
    Exit-PSSession
    ```

### Task 2: Disable PowerShell Remoting

1.  Switch to **LON-CL1**.

2.  Sign in to **LON-CL1** as **adatum\\Administrator** with the password: **Pa55w.rd**.

3.  Right-click **Start**, and then select **Windows PowerShell (Admin)**.

4.  In the Administrator: Windows PowerShell window, type the following command, and then press **Enter**:

    ```
    Disable-PSRemoting -Force
    ```

5.  Select the **File Explorer** icon on the taskbar, browse to **Documents** and double-click **remote.txt**.

6.  Close all open windows.

7.  Switch to **LON-CL2**

8.  In the Windows PowerShell window, type the following command, and then press **Enter**:

    ```
    Invoke-Command -ComputerName LON-CL1 -ScriptBlock {Get-ChildItem "C:\Program Files"}
    ```

    _Note: The command is failing now._

9.  Close all open windows.


### Task 3: Enable Remote Desktop

1.  Switch to **LON-CL1**.

2.  Select **Start**, and then Select the **Settings** icon.

3.  In **Settings**, select **System**.

4.  On the **System** tab, select **Remote Desktop**.

5.  Switch **Enable Remote Desktop** on.

6.  In the Remote Desktop Settings window select **Confirm**.

7.  Close the **Settings** app.

**Results**: After completing this exercise, you will have enabled and tested the remote management functions of windows.

**END OF LAB**