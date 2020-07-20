# Practice Lab: Troubleshooting Application Compatibility Issues

## Summary

In this exercise, you will learn to use the Application Compatibility Toolkit to create a compatibility fix for an application that does not natively run on Windows 10.

### Scenario

Benjamin has filed an incident report that states that the Stock Viewer application is not working after the upgrade to Windows 10. Your manager indicates that the application is not fully compatible with Windows 10, and that you should investigate if ACT can mitigate this, which is already installed on LON-CL1.

### Task 1: Identify compatibility issues

1. If necessary, sign in to **LON-CL1** as **Adatum\\Benjamin** with the
    password **Pa55w.rd**.

1. On the desktop, on the taskbar, select the **File Explorer** icon.

1. Navigate to **C:\\Program Files (x86)\\StockViewer**, and then double-click
    **StockViewer**.

1. In the Permission denied dialog box, select **OK**.

1. On the Stock Viewer toolbar, select **Trends**.

1. In the Error dialog box, select **OK**.

1. On the Tools menu, select **Options**.

1. In the Stock Viewer dialog box, select **Continue**.

1. On the Tools menu, select **Show Me a Star**.

1. In the Unsupported Version dialog box, select **OK**.

1. **Close** Stock Viewer.

1. If a Program Compatibility Assistant window opens, select **This program ran
    correctly**.

1. In the File Explorer window, right-click **StockViewer**, and then select
    **Run as administrator**.

1. In the User Account Control dialog box, provide the following credentials,
    and then select Yes:
    - Username: **Adatum\\Administrator**
    - Password: **Pa55w.rd**

1. On the Stock Viewer toolbar, select **Trends**.

1. On the Tools menu, select **Options**, and then select **OK**.

1. On the Tools menu, select **Show Me a Star**, and then select **OK**.

1. Close Stock Viewer, and then sign out of **LON-CL1**.

### Task 2: Create a compatibility fix

1. Sign in to **LON-CL1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

1. Click the Start button. In the list of apps, select **Windows Kits**, and
    then select **Compatibility Administrator (32bit)**.

1. In the **Compatibility Administrator (32-bit) – New Database (1)
    \[Untitled_1\]** dialog box, right-click **New Database(1) \[Untitled_1\]**, and
    then select **Rename**.

1. Type **AdatumACT**, and then press **Enter**.

1. In the Compatibility Administrator window, right-click **AdatumACT
    \[Untitled_1\]\*,** select **Create New**, and then select **Application Fix**.

1. In the Create New Application Fix Wizard, in the Name of the program to be
    fixed text box, type **StockViewer**.

1. Select **Browse**.

1. In the Find Binary window, browse to **C:\\Program Files
    (x86)\\StockViewer\\StockViewer.exe**, and then select **Open**.

1. In the Create new Application Fix window, select **Next**.

1. On the Compatibility Modes page, select the **Run this program in
    compatibility mode** for check box, select the **drop-down list**, and then
    select **Windows XP**.

1. In the Additional compatibility modes section, scroll down, select the
    **RunAsAdmin** check box, and then select **Next**.

1. On the Compatibility Fixes page, select **Next**.

1. On the Matching Information page, select **Finish**.

1. In the Compatibility Administrator window, select **Save**.

1. In the Save Database window, browse to **c:\\**.

1. In the File name text box, type **AdatumACT**, and then select **Save**.

1. Close the Compatibility Administrator window.

1. Sign out of **LON-CL1**.

### Task 3: Test the compatibility fix

1. Sign in to **LON-CL1** as **Adatum\\Benjamin** with the password
    **Pa55w.rd**.

1. Click **Start**, and type **cmd**, right-click on **Command Prompt**, and
    select **Run as Administrator**.

1. In the User Account Control dialog box, enter the following credentials, and then select **Yes**:
    - Username: **Adatum\\administrator**
    - Password: **Pa55w.rd**

1. At the command prompt, type the following command, and then press **Enter**:

    ```bat
    Sdbinst C:\\AdatumACT.sdb
    ```

1. On the desktop, on the taskbar, select the **File Explorer** icon.

1. In File Explorer, navigate to **C:\\Program Files (x86)\\StockViewer** and
    then double-click **StockViewer**.

1. In the User Account Control dialog box, enter the following credentials, and then select **Yes**:
    - Username: **Adatum\\administrator**
    - Password: **Pa55w.rd**

1. On the Stock Viewer toolbar, select **Trends**.

1. On the Tools menu, select **Options**.

1. Click **OK** to close the message box.

1. On the Tools menu, select **Show Me a Star**, and then select the star.

1. **Close** the Stock Viewer application.

1. If the Program Compatibility Assistant window opens, select **Yes**, this
    program worked correctly.

1. Sign out of **LON-CL1**.

**Results**: After completing this exercise, you should have successfully resolved the issues with the Stock Viewer application.

## END OF LAB
