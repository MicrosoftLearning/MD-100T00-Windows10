# Practice Lab: Recovering using Reset This PC

## Summary

During this lab you will learn how to recover a Windows device using Reset This
PC.

### Scenario

You discover that your Windows device is having intermittent issues with an
application on LON-CL2. Repeated attempts have been made to correct the issue,
but have been unsuccessful. You've decided to try resetting the PC. You would
like to still retain the user files on the PC.

### Task 1: Use the Reset this PC option

1.  Sign in to **LON-CL2** as **Adatum\\Administrato**r with the password of
    **Pa55w.rd**.

2.  On **LON-CL2**, right-click the desktop, point to **New**, select **Text
    Document**, type **Report** as its name, and then press Enter.

3.  Right-click the **Start** icon, select **Windows PowerShell**.

4.  In the **Windows PowerShell** prompt, type ipconfig /all and then press
    **Enter.**

5.  Verify that the Ethernet connection is not Dynamic Host Configuration
    Protocol–enabled (DHCP-enabled) and that it has the IPv4 address
    172.16.0.41.

6.  In the Windows PowerShell prompt, type `sysdm.cpl` and then press **Enter**.

7.  Verify that the device name is **LON-CL2** and that it is in the
    **Adatum.com** domain.

8.  In the Windows PowerShell prompt, type shutdown /r /o, and then press
    **Enter**.

9.  In the **You’re about to be signed out** dialog box, select **Close** and
    wait for the restart.

10. On the **Choose an option** page, select **Troubleshoot**.

11. On the **Troubleshoot** page, select **Reset this PC**.

12. On the **Reset this PC** page, select **Keep my files**, and wait while the
    computer restarts.

13. On the **Reset this PC** page, select **Admin**. In the **Enter the password
    for this account** box, enter **Pa55w.rd**, select **Continue**, and then
    select **Reset**.

14. Wait for the reset to complete.



### Task 2: Verify that Reset this PC was successful

1.  Sign in to **LON-CL2** as **Adatum\\Administrator** with the password of
    **Pa55w.rd**.

2.  In LON-CL2 check if the file Report.txt is still available on the desktop.

3.  Right-click the **Start** icon, select **Windows PowerShell**.

4.  In the **Windows PowerShell** prompt, type `ipconfig /all` and then press
    **Enter**,

5.  Verify that the Ethernet connection is now Dynamic Host Configuration
    Protocol–enabled (DHCP-enabled).

6.  In the Windows PowerShell prompt, type `sysdm.cpl` and then press **Enter**.

7.  Verify that the device name is LON-CL2 and that it is in the Adatum.com
    domain.

8.  Close all open windows.



**Results**: After completing this exercise, you should have successfully
recovered your devices using Reset This PC

**END OF LAB**