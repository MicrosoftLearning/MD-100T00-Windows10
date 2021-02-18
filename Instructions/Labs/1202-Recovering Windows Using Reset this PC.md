# Practice Lab: Recovering Windows using Reset This PC

## Summary

During this lab you will learn how to recover a Windows 10 device using Reset This PC.

### Scenario

You discover that SEA-CL2 is having intermittent issues. Repeated attempts have been made to correct the issues, but have been unsuccessful. You've decided to try resetting the PC. You would like to still retain the user files on the PC.

### Task 1: Use the Reset this PC option

1. Sign in to **SEA-CL2** as **Contoso\\Administrator** with the password of **Pa55w.rd**.
2. On **SEA-CL2**, right-click the desktop, point to **New**, select **Text Document**, type **Report** as its name, and then press Enter.
3. Right-click the **Start** icon, select **Windows PowerShell**.
4. In the **Windows PowerShell** prompt, type **ipconfig /all** and then press **Enter.**
5. Verify that the Ethernet connection is not Dynamic Host Configuration Protocol–enabled (DHCP-enabled) and that it has the IPv4 address 172.16.0.45.
6. In the Windows PowerShell prompt, type `sysdm.cpl` and then press **Enter**.
7. Verify that the device name is **SEA-CL2** and that it is in the **Contoso.com** domain.
8. Select **Start**, select **Settings**, and then select **Update & Security**.
9. In the **Update & Security** navigation pane, select **Recovery**.
10. On the Recovery page, under **Reset this PC**, select **Get started**.
11. On the Rest this PC dialog box, select **Keep my files**.
12. On the Ready to reset this PC page, select **View apps that will be removed**. Take note of the apps and then select **Back**.
13. On the Ready to reset this PC page, select **Reset**.
14. Wait for the reset to complete. It will take a while to complete.

### Task 2: Verify that Reset this PC was successful

1. Sign in to **SEA-CL2** as **Contoso\\Administrator** with the password of **Pa55w.rd**.
2. Verify that the file Report.txt is still available on the desktop.
3. On the desktop, double-click the **Removed Apps** report and verify the apps that have been removed while resetting the PC.
4. Close Microsoft Edge.
5. Right-click the **Start** icon, select **Windows PowerShell**.
6. At the **Windows PowerShell** prompt, type `ipconfig /all` and then press **Enter**.
7. Verify that the Ethernet connection is now Dynamic Host Configuration Protocol–enabled (DHCP-enabled).
8. In the Windows PowerShell prompt, type `sysdm.cpl` and then press **Enter**.
9. Verify that the device name is SEA-CL2 and that it is in the Contoso.com domain.
10. Close all open windows.

**Results**: After completing this exercise, you will have successfully recovered SEA-CL2 by using Reset This PC.

**END OF LAB**