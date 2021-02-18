# Practice Lab: Configuring Network Connectivity

## Summary

In this lab, you will identify IPv4 settings and validate connectivity on a Windows 10 device. You will also configure a Windows 10 device to automatically obtain IPv4 settings from a DHCP service.

## Exercise 1: Verifying and Testing IPv4 Settings

### Scenario

You need to identify the current static IPv4 settings on SEA-CL1. You also need to test connectivity from SEA-CL1 to SEA-DC1.

### Task 1: Verify IPv4 settings from Settings and the Network and Sharing Center

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**.

2. Select the **Network** icon in the notification area, and then select **Network & Internet settings**.

3. In the **Settings** window, on the **Status** page, select **Properties**.

4. Scroll down and identify the **IP settings** and **Properties** for the network adapter. The following information should be available:

   - IPv4 address
   - IPv4 subnet prefix length
   - IPv4 DNS servers
   - IPv4 gateway

   *Also take note that the IP assignment is set to Manual, which indicates that this is a static IP address assignment.*

5. Under **IP settings**, select **Edit**. Notice that you can modify the IPv4 and IPv6 settings.

6. Select **Cancel** to close the **Edit IP settings** window.

7. Select the **Back** button and then select **Status**.

8. In the Status details pane, scroll down and then select **Network and Sharing Center**. Notice the domain and connection information.

9. In **Network and Sharing Center**, to the right of the Contoso.com Domain network, select **Ethernet**.

10. In the **Ethernet Status** dialog box, select **Details**. This window displays the same configuration information for this adapter as the Settings status page.

11. In the **Network Connection Details** window, select **Close**.

12. In the **Ethernet Status** dialog box, select **Properties**. You can configure protocols in this window.

13. Select **Internet Protocol Version 4 (TCP/IPv4)**, and then select **Properties**.

    _Note: You can configure the IP address, subnet mask, default gateway, and Domain Name System (DNS) servers in this window._

14. Select **Cancel** and then close all open windows without modifying any settings.

### Task 2: Verify IPv4 settings from the command line

1. On SEA-CL1, right-click **Start**, and then select **Windows PowerShell (Admin)**.

2. At the Windows PowerShell command prompt, type following command, and then press **Enter**.

    ```powershell
    Get-NetIPAddress
    ```

    _Note: The IPv4 address from the Ethernet interface should match what you identified earlier._

3. At the Windows PowerShell command prompt, type the following command, and then press **Enter**.

    ```powershell
    netsh interface ipv4 show config
    ```

    _Note: The current IPv4 configuration is displayed and should match what you identified earlier._

4. At the Windows PowerShell command prompt, type the following command, and then press Enter.

    ```powershell
       ipconfig /all
    ```

    _Note: Again, the information should match what you identified earlier._
5. Leave the **Administrator: Windows PowerShell** window open.

### Task 3: Test connectivity

1. At the Windows PowerShell command prompt, type the following command, and then press **Enter**.

    ```powershell
    Test-Connection SEA-DC1
    ```

2. At the Windows PowerShell command prompt, type the following command, and then press **Enter**.

    ```powershell
    ping SEA-DC1
    ```

3. At the Windows PowerShell command prompt, type type the following command, and then press **Enter**.

    ```powershell
    PathPing SEA-DC1
     ```

4. Observe and describe the differences between the three connectivity tests performed.

   _Note: Test-Connection and Ping provides information on time and success of connectivity directly to a target host. PathPing provides statistics on how many connections it takes to route to a target host._

5. Close the Windows PowerShell window.

**Results**: After completing this exercise you have verified the IPv4 settings of a windows device and used various tools to test connectivity.

## Exercise 2: Configuring Automatic IPv4 Settings

### Scenario

Your network administrative team has configured DNS and DHCP services located on SEA-DC1. You need to reconfigure SEA-CL1 to obtain its IPv4 settings using the DHCP service. You will then test and verify the connectivity between SEA-CL1 and SEA-DC1 using the newly obtained IPv4 address settings.

### Task 1: Reconfigure the IPv4 settings

1. On **SEA-CL1**, select the **Network** icon in the notification area, and then select **Network & Internet settings**.

2. Select **Network and Sharing Center**.

3. In **Network and Sharing Center**, to the right of the Contoso.com Domain network, select **Ethernet**.

4. In the **Ethernet Status** dialog box, select **Properties**.

5. Select **Internet Protocol Version 4 (TCP/IPv4)**, and then select **Properties**.

6. In the **Internet Protocol Version 4 (TCP/IPv4) Properties** dialog box, select **Obtain an IP address automatically**.

7. Select **Obtain DNS server address automatically**.

8. Select **OK** to save the changes.

9. In the **Ethernet Properties** dialog box, select **Close**.

10. In the **Ethernet Status** dialog box, select **Details**. Notice that DHCP is enabled, and that the IP address of the DHCP server displays.

11. On SEA-CL1, right-click **Start**, and then select **Windows PowerShell (Admin)**.

12. At the Windows PowerShell command prompt type the following command, and then press **Enter**.

    ```powershell
    ipconfig /all
    ```

13. Verify that the IPv4 address is obtained from DHCP.

### Task 2: Test connectivity

1. At the Windows PowerShell command prompt, type type the following command, and then press **Enter**.

    ```powershell
    Test-Connection SEA-DC1
    ```

    _Note: You should receive four replies from SEA-DC1._
2. Close all open windows.
3. Sign out of SEA-CL1.

### Task 3: View the impact on the DHCP server

1. Switch to **SEA-SVR1**.
2. Sign in to SEA-SVR1 as **Contoso\\Administrator** with the password **Pa55w.rd**.
3. Select **Start** and then select **Server Manager**.
4. In **Server Manager**, select **All Servers**, right-click **SEA-DC1**, and then select **DHCP Manger**.
5. In **DHCP**, expand **SEA-DC1.Contoso.com**, expand **IPv4**, expand **Scope [172.16.0.0] Contoso**, and then select **Address Leases**.
6. In the details pane, you should see the address lease for the SEA-CL1 Windows 10 client.
7. Close the DHCP window.
8. Sign out of SEA-SVR1.

**Results**: After completing this exercise you have configured a Windows device to automatically obtain IPv4 settings from a DHCP service.

**END OF LAB**