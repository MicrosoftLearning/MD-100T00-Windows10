# Practice Lab: Creating Firewall Rules

## Summary

In this exercise you will learn how to create and configure firewall rules to block and allow specific service connections to a device.

_**Dependency Notice**: Remote Desktop must be enabled on LON-CL1 if the Remote Management lab was not performed._

## Exercise 1: Creating and Testing Inbound Rules  

### Scenario

Your security officer has requested that users on LON-CL2 are not allowed to remote desktop into LON-CL1 whereas users from other devices are allowed.

### Task 1: Test existing functionality

1. Sign in to **LON-CL2** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

1. Select **Start**, type **mstsc.exe**, and then press **Enter**.

1. In the Computer box, type **LON-CL1**, and then press **Enter**.

1. In the Windows Security dialog, in the password box enter **Pa55w.rd**, and then select **OK**

1. Select **Start** on **LON-CL1**, select **Administrator**, and then
    select **Sign out**.

### Task 2: Create an inbound rule

1. Switch to **LON-CL1**.

1. Sign in to **LON-CL1** as **Adatum\\Administrator** with the password **Pa55w.rd**.

1. Select **Start**, and type **control**, then select **Control Panel**.

1. Select **System and Security**, and then select **Windows Defender Firewall**.

1. In the left pane, select **Advanced settings**, select **Inbound Rules**, and
    then select **New Rule**.

1. In the New Inbound Rule Wizard window, select **Predefined**, select the
    **drop-down list**, select **Remote Desktop**, and then select **Next**.

1. On the Predefined Rules page, **check all available rules**, and then select
    **Next**.

1. On the Action page, select **Block the connection**, and then select **Finish**.

1. **Minimize** the Windows Firewall with Advanced Security window.

### Task 3: Test the rule

1. Switch to **LON-CL2**.

1. Select **Start**, type **mstsc.exe**, and then press **Enter**.

1. In the Computer box, type **LON-CL1**, and then press **Enter**.

1. In the Remote Desktop Connection window, select **OK**.

1. Verify that the connection attempt fails.

1. Close all open windows.

**Results**: After completing this exercise, you should have created and verified inbound firewall rules.

## Exercise 2: Creating and Testing Outbound Rules

### Scenario

LON-DC1 also needs to be configured to allow remote desktop connections, however LON-CL1's configuration should not allow remote desktop connections to LON-DC1.

### Task 1: Test existing functionality

1. **Switch to LON-DC1**

1. Sign in to **LON-DC1** as **Adatum\\Administrator** with the password  **Pa55w.rd**

1. Right-click **Advanced System Settings**.

1. In the System Properties window select the **Remote** tab.

1. Select **Allow remote connections to this computer** and select **OK**.

1. Close the **System** window.

1. Switch to **LON-CL1**.

1. Select **Start**, type **mstsc.exe**, and then press **Enter**.

1. In the Computer box, type **LON-DC1**, and then press **Enter**.

1. In the Windows Security dialog, in the password box enter  **Pa55w.rd**, and then select **OK**

1. Select **Start** on **LON-DC1**, select **Administrator**, and then select **Sign out**.

### Task 2: Create an outbound rule

1. On **LON-CL1**, on the taskbar, select the **Windows Firewall with Advanced
    Security** window, and then select **Outbound Rules**.

1. In the Actions pane, select **New Rule**.

1. On the Rule Type page, verify that you are creating a **Program rule**, and
    then select **Next**.

1. On the Program page, browse and select **C:\\Windows\\System32\\mstsc.exe**,
    select **Open**, and then select **Next**.

1. On the Action page, verify that the action is **Block the Connection**, and
    then select **Next**.

1. On the Profile page, verify that **all profiles are checked**, and then
    select **Next**.

1. On the Name page, type **Block Outbound RDP to LON-DC1** in the Name box,
    and then select **Finish**.

1. In the Windows Firewall with Advanced Security window, select the **Block
    Outbound RDP to LON-DC1** rule, and then in the Actions pane, select
    **Properties**.

1. Select the **Scope tab**, and then under the **Remote IP address heading**,
    select the **These IP addresses** option.

1. Under the Remote IP address heading, select **Add**, in the This IP address
    or subnet box, type **172.16.0.10**, and then select **OK**.

1. In the Block Outbound RDP to LON-DC1 Properties dialog box, select **OK**.

### Task 3: Test the rule

1. Select **Start**, type **mstsc.exe**, and then press **Enter**.

1. In the Computer box, **type LON-DC1**, and then press **Enter**.

1. In the Remote Desktop Connection dialog box, select **OK**.

1. Verify that the connection attempt fails

1. **Close** all open windows.

**Results**: After completing this exercise, you should have created and tested outbound firewall rules.

## END OF LAB
