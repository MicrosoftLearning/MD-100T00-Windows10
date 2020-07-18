# Practice Lab: Configuring Network Connectivity

## Summary

In this exercise, you will verify and test the initial network settings of a
Windows 10 device.

## Exercise 1: Verifying and Testing IPv4 Settings

### Scenario

Before delivering the first batch of Windows 10 devices to your users, you
decide to test them on a secure test network. You have installed on LON-DC1 a
domain controller and deployed the DHCP and DNS Server roles within the test
environment. You must configure the IP network settings on your Windows 10
devices.

### Task 1: Verify the IPv4 settings from the Network and Sharing Center

1. Sign in to **LON-CL1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

1. Select the **Network** icon in the notification area, and then select
    **Network & Internet settings**.

1. Scroll down, and select **Network and Sharing Center**.

1. In **Network and Sharing Center**, to the right of the **Adatum.com Domain
    network**, select **Ethernet**.

1. In the **Ethernet Status** dialog box, select **Details**. This window
    displays the same configuration information for this adapter as would the
    **Ipconfig** command.

1. Record the following information:

    - IPv4 Address

    - IPv4 Subnet Mask

    - IPv4 DNS Server

1. In the **Network Connection Details** window, select **Close**.

1. In the **Ethernet Status** dialog box, select **Properties**. You can
    configure protocols in this window.

1. Select **Internet Protocol Version 4 (TCP/IPv4)**, and then Select
    **Properties**.

    _Note: You can configure the IP address, subnet mask, default gateway,
    and Domain Name System (DNS) servers in this window._

1. Close all open windows without modifying any settings.

### Task 2: Verify the current IPv4 settings from the command line

1. Right-click **Start**, and then select **Windows PowerShell (Admin)**.

1. At the Windows PowerShell command prompt, type following command, and then
    press **Enter**.

    ```pwsh
    Get-NetIPAddress
    ```

    _Note: The IPv4 address from the Ethernet interface should match what you
    recorded earlier._

1. At the Windows PowerShell command prompt, type the following command, and
    then press **Enter**.

    ```pwsh
    netsh interface ipv4 show config
    ```

    _Note: The current IPv4 configuration is displayed and should match what
    you recorded earlier._

1. At the Windows PowerShell command prompt, type the following command, and
    then press Enter.

    ```pwsh
    ipconfig /all
    ```

    _Note: Again, the information should match what you recorded earlier._

1. Leave the **Administrator: Windows PowerShell** window open.

### Task 3: Test connectivity

1. At the Windows PowerShell command prompt, type the following command, and
    then press **Enter**.

    ```pwsh
    Test-Connection LON-DC1
    ```

1. At the Windows PowerShell command prompt, type type the following command, and then press
    **Enter**.

    ```pwsh
    netstat -n
    ```

1. Observe and describe the active connections to 172.16.0.10.

    _Note: Most connections to services are transient._

1. If no connections appear, create a connection. To create a connection, in
    the Type here to search box, type **\\\\LON-DC1**, and then press Enter.

1. In File Explorer, double-click **NETLOGON**.

1. At the Windows PowerShell command prompt, type the following command, and then press
    **Enter**.

    ```pwsh
    netstat -n
    ```

1. Identify the services that LON-CL1 had connections to on LON-DC1.

**Results**: After completing this exercise you have verified the IP4 settings
of a windows device.

### Scenario 2

After preparing the DNS and DHCP server you will configure LON-CL1 to obtain its
IPv4 settings through DHCP. Then you will test the connectivity and verify the
obtained DHCP lease on the DHCP server LON-DC1.

## Exercise 2: Configuring Automatic IPv4 Settings

### Task 1: Reconfigure the IPv4 settings

1. On **LON-CL1**, Select the **Network** icon in the notification area, and
    then select **Network & Internet settings**.

1. Select **Network and Sharing Center**.

1. In **Network and Sharing Center**, to the right of the **Adatum.com Domain**
    network, select **Ethernet**.

1. In the **Ethernet Status** dialog box, select **Properties**. In this
    window, you can configure protocols.

1. Select **Internet Protocol Version 4 (TCP/IPv4)**, and then select
    **Properties**.

1. In the **Internet Protocol Version 4 (TCP/IPv4) Properties** dialog box,
    select **Obtain an IP address automatically**.

1. Select **Obtain DNS server address automatically**.

1. Select **OK** to save the changes.

1. In the **Ethernet Properties** dialog box, select **Close**.

1. In the **Ethernet Status** dialog box, select **Details**. Notice that
    Dynamic Host Configuration Protocol (DHCP) is enabled, and that the IP
    address of the DHCP server displays.

1. Switch to the Windows PowerShell command prompt.

1. At the Windows PowerShell command prompt type the following command, and
    then press **Enter**.

    ```pwsh
    ipconfig /all
    ```

1. Verify that the IPv4 address is obtained from DHCP.

### Task 2: Test connectivity

1. At the Windows PowerShell command prompt, type type the following command, and
    then press **Enter**.

    ```pwsh
    Test-Connection LON-DC1
    ```

1. At the Windows PowerShell command prompt, type the following command, and then press
    **Enter**.

   ```pwsh
   netstat -n
   ```

   Observe and describe the active connections to 172.16.0.10.

   _Note: Most connections to services are transient._

1. Note that no connections display. To create a connection, in the **Type here
    to search** box, type **\\\\LON-DC1**, and then press Enter.

1.  In **File Explorer**, double-click **NETLOGON**.

1.  At the Windows PowerShell command prompt, type type the following command, and then press
    **Enter**.

    ```pwsh
    netstat -n
    ```

1. Identify the services that **LON-CL1** had connections to on **LON-DC1**.

1. Close all open windows.

### Task 3: View the impact on the DHCP server

1. Switch to **LON-DC1**.

1. Sign in to LON-CL1 as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

1. In **Server Manager**, select **Tools**, and then select **DHCP**.

1. In **DHCP**, expand **lon-dc1.adatum.com**, expand **IPv4**, expand **Scope
    [172.16.0.0] Adatum**, and then select **Address Leases**.

1. In the details pane, you should see the address lease for your Windows 10
    client.

1. Close the DHCP window.

**Results**: After completing this exercise you have configured the IP4 settings
of a windows device to use DHCP.

## END OF LAB
