# Practice Lab: Using PowerShell to Configure Windows

 

## Summary

In this lab you will learn how to use PowerShell to Configure Windows.

 
**Note**: In Windows PowerShell, a hyphen (-) precedes each cmdlet parameter
name, as with the -Value parameter in the preceding code. When you copy text
from a file, word wrapping might separate the hyphen from the parameter name.
Therefore, inspect all copied cmdlets and parameters to ensure that they follow
the Windows PowerShell syntax requirements.

 
### Scenario

Your supervisor, Mr. Meadows, wants you to use Windows PowerShell to test the
scripting environment. So you run several PowerShell commands on LON-CL1 to get
familiar with the syntax and create a script to list all running services using
the PowerShell ISE.

 

### Task 1: Use Windows PowerShell to configure a device

1.  Sign in to **LON-CL1** as **Adatum\\Administrato**r with the password
    **Pa55w.rd.**

2.  Select **Start** and type **PowerShell**. Select **Run as administrator**.
    In the User Account Control window select **Yes**.

3.  At the PowerShell window, type the following and then press **Enter**:

```
Get-ExecutionPolicy
```

4.  Confirm the current setting of the PowerShell execution policy is set to
    **Restricted.**

5.  If the execution policy is set to **Restricted**, change it to
    **Unrestricted** by running the following command at the PowerShell window:

```
Set-ExecutionPolicy Unrestricted
```

6.  Confirm that the execution policy is now **Unrestricted**.

7.  At the PowerShell window, launch Notepad by typing the following command and
    then press **Enter**:

```
Start-Process Notepad
```

8.  At the PowerShell window, type the following command and then press
    **Enter**:

```
Get-Process
```

1.  Review the list of all running processes. Identify that Notepad is running
    and note the Process ID.

9.  At the PowerShell window, type the following command and then press
    **Enter**:

```
Stop-Process -Id [ID]
```

10.  Verify that the Notepad window is no longer open.

11.  At the PowerShell window, list the application log entries by typing the
    following command and then press **Enter**:

```
Get-EventLog -LogName "Application"
```

12.  Select **Start** and type **Telnet**. Select **Turn Windows features on and
    off**.

13.  In the Windows Features window verify that **Telnet Client** is not
    selected.

14. At the PowerShell Window, type the following command, and then press **Enter**:
    
```
Enable-WindowsOptionalFeature -Online -FeatureName "TelnetClient"
```

_Note: This will install the Telnet Client windows feature._

15.  Select **Start** and type **Telnet**. Select **Open**.

16.  Close all open windows.


### Task 2: Use a Windows PowerShell Script

1.  In the **Type here to search** box, type
    [\\\\LON-DC1\\Labfiles](file:///\\LON-DC1\Labfiles), and then press Enter.

2.  In the content pane, double-click the **Configure** folder.

3.  Copy the **Services.ps1** file into the E: \\Labfiles folder on LON-CL1.

4.  Select **Start** and type **Powershell ISE**. Press **Enter**.

5.  In the Windows PowerShell ISE, open the script file
    **E:\\Labfiles\\Services.ps1**.

6.  Read the script, and then note what the script is doing, according to the
    following note.

    -   _Note:_
    -   _Comments are green._
    -   _Variables are red._
    -   _Cmdlets are bright blue._
    -   _Text in quotation marks is dark red._

7.  Select line 3 in the script, and then select **Run selection (F8)**.

    _Note: Only the command in line 3 will be executed._

8.  Select **Run script (F5)**, and then read the output.

    _Note: The output does not have multiple colors._

9.  At the end of line 14, type **–ForegroundColor \$color**

10. On the toolbar, select **Run script (F5)** in the Windows PowerShell ISE
    window. Select **OK** to save the file, and then read the output.

    _Note: Running services are green, and services that are not running are
    red._

11. On line 16, type **Write-Host "A total of" \$services.count "services were
    evaluated"**

12. Select **Run script (F5)**, and in the Windows PowerShell ISE window select
    **OK**.

13.  Select **Show Command Add-on** in the PowerShell ISE toolbar.

14. In the **Commands** pane, build a **Write-Host** cmdlet with the following
    options:

    -   BackgroundColor: **Gray**

    -   ForegroundColor: **Black**

    -   Object: **"Script execution is complete"**

15. Select **Copy** and paste the command to line 17 of the script.

16. Select **Run script (F5)**, and in the Windows PowerShell ISE window select
    **OK**

17. Select **Start** and type **PowerShell**. Press **Enter**.

18. At the PowerShell window, type the following command and then press
    **Enter**:

```
Set-Location E:\Labfiles
```

13. At the PowerShell window, type the following and then press **Enter**:

```
.\Services.ps1
```

14. Close all open windows.

 

**Results:** After completing the exercise you have learned how to manage
Windows 10 using PowerShell and PowerShell scripts.

**END OF LAB**