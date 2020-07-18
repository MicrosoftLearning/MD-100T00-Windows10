# Practice Lab: In-place upgrade of Windows 7 to Windows 10

## Summary

In this lab, verify the client meets upgrade requirements and performed an in-place upgrade of Windows 7 to Windows 10.

### Scenario

As Windows 7 is reaching end of support in the near future your manager wants you to upgrade your company's laptops to Windows 10. As most of the hardware is relatively new, you decided to use an in-place upgrade on LON-CL6.

### Task 1: Verify that the computer meets the minimum requirements

1. Sign in to LON-CL6 as **Adatum\\Administrator** with the password **Pa55w.rd**

1. If a Microsoft Windows dialog box opens, select **Restart Later**.

1. If a Windows Activation dialog box opens, Select **Ask me later**. Select
    **OK**.

1. On the taskbar, Select **Start**. Right-click **Computer**, and then Select
    **Properties**.
1. Write down the settings for:
   - Processor: \____________________\_
   - Installed memory (RAM):\____________\_

1. **Close** the System window.

1. Right-click **the desktop**, and then select **Screen resolution**.

1. Write down the screen resolution: \________________\_

1. On the taskbar, select the **Windows Explorer** icon.

1. Click **Computer**
   - Write down the available disk space for drive C: \_______________\_
   - Do the noted values match the minimum requirements? \_______________\_

### Task 2: Perform an in-place upgrade from local media

1. Sign in to LON-CL6 as **Adatum\\Administrator** with the password **Pa55w.rd**

1. If a Microsoft Windows dialog box opens, select **Restart Later**.

1. If a Windows Activation dialog box opens, select **Ask me later**. Select
    **OK**.

1. On the taskbar, select the **Windows Explorer** icon.

1. In Windows Explorer, select the **DVD drive**.

1. In the contents pane, double-click the **setup.exe** file.

1. On the Windows 10 Setup page, select **Next**.

1. On the Applicable notices and license terms page, select **Accept**.

1. On the Ready to install page, select **Change what to keep**.

1. On the Choose what to keep page, select **Nothing**. Select **Next**, and then
    select **Yes**.

1. On the Ready to install page, select **Install**. The setup program will now upgrade your Windows 7 installation to Windows 10.

_Note: This will take approximately 30 minutes._

### Task 3: Complete the Installation

1. On the Region page, select **Yes**.

1. On the Keyboard Layout page, select **Yes**, then **Skip**.

1. On the Sign in with Microsoft page, select **Domain join instead**.

1. On the Who’s going to use this PC page, provide the following information when prompted, and selecting **Next**
   - Username: **LocalAdmin**
   - Password: **Pa55w.rd**

1. When prompted for security questions, select any three questions and enter any answer.

1. On the Do more across devices with activity history, select **No**.

1. On the Get help from your digital assistant, select **Decline**

1. On the choose privacy settings for your device, select **Accept**.

1. Wait for the installation to complete.

### Task 4: Verify that the upgrade was successful

1. Select **Start** and type **winver**. Press **Enter**.

1. Make sure that the version number is 1809.

**Results**: After finishing this exercise, you will have successfully upgrading LON-CL6 from Windows 7 to Windows 10.

### END OF LAB
