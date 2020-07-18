# Practice Lab: Updating Windows 10

## Summary
In this lab you will learn how to manage the settings of Windows Update.


## Exercise 1: Configuring Updates for a Single Device

### Scenario

Your IT security officer discovers that not all devices are doing properly Windows 10 updates. So you will configure the settings for Windows Update on LON-CL1 to receive updates from the Semi-Annual Channel (Targeted) release channel.

### Task 1: Configure update settings for a single device

1.  Sign in to **LON-CL1** as ADATUM\\Administrator with the Password **Pa55w.rd**

2.  Right-click **Start**, and then select **Windows PowerShell (Admin)**. In the    **User Account Control** window select **Yes**.

3.  In the Administrator: Windows PowerShell window, type the following command,
    and then press Enter:

```
Set-Service wuauserv -StartupType Manual
```

_Note: For the lab setup, the Windows Update service is disabled. The above command is not necessary to run in typical Windows 10 scenarios._

4.  Select **Start**, and then Select the **Settings** icon.

5.  In **Settings**, select **Update & Security**.

6.  On the **Windows Update** tab, select **Advanced options**.

7.  On the Advanced options page, scroll down and in the **Semi-Annual Channel (Targeted)** drop-down list, verify that **Semi-Annual Channel** is selected.

    _Note: The Semi-Annual Channel (Targeted) is removed in v1903._

8.  Select **Delivery Optimization**.

9.  On the Delivery Optimization page, verify that the **Allow downloads from other
    PCs** option is enabled.

10.  Select **PCs on my local network, and PCs on the Internet**, and then select
    **Back** twice.

11.  In the navigation pane, select **Windows Insider Program**. Notice that the
    **Get Started** option is not available.

12.  In the navigation pane, select **Windows Update**.

### Task 2: Review applied updates

1.  On the **Windows Update** page, select **View update history**.

2.  Review the updates listed, and then select **Uninstall updates**.

3.  Review the updates listed in **Installed Updates**. Close **Installed
    Updates**.

4.  On the **View Update history** page, select **Back**.

**Results**: After completing this exercise, you will have successfully configured and/or confirmed Windows Update settings.

## Exercise 2: Configuring Updates with GPOs

### Scenario

To prevent other users from modifying the settings for Windows update on LON-CL1 you will create a local Group Policy Object (GPO) that will apply the intended settings.


### Task 1: Configure update settings by using GPOs

1.  In the **Type here to search** box, type **gpedit.msc**, and then press Enter.

2.  In **Local Group Policy Editor**, navigate to **Computer
    Configuration/Administrative Templates /Windows Components/Data Collection
    and Preview Builds**.

3.  In the right pane, double-click **Toggle user control over Insider builds**.

4.  In the **Toggle user control over Insider builds** dialog box, select
    **Disabled**, and then select **OK**.

5.  In **Local Group Policy Editor**, navigate to **Computer
    Configuration/Administrative Templates /Windows Components/Windows
    Update/Windows Update for Business**.

6.  In the right pane, double-click **Select when Preview Builds and Feature
    Updates are received.**

7.  In the **Select when Preview Builds and Feature Updates are received** dialog
    box, select **Enabled**.

8.  In the **Select Windows Readiness level** for the updates you want to
    receive drop-down list, **select Semi-Annual Channel (Targeted)**, and then
    select OK.

9.  In the navigation pane, select **Windows Update**.

10. In the right pane, double-click **Do not connect to any Windows Update
    Internet locations**.

11. In the **Do not connect to any Windows Update Internet locations** dialog
    box, select **Enabled**, and then select **OK**.

12. Close **Local Group Policy Editor**.

### Task 2: Verify that the device’s update settings are managed centrally  

1.  Select **Start**, type **cmd**. Right-click on **Command Prompt** and select
    **Run as Administrator**.

2.  In the command prompt, type **gpupdate /force**, and then press Enter.

3.  Switch to **Settings**.

4.  In the navigation pane, select **Windows Insider Program**.

5.  On the **Windows Insider Program** tab, notice that the option to **Get
    started with Insider builds** is unavailable.
    
6.  Close all open windows.

**Results**: After completing this exercise, you will have successfully configured and/or confirmed Group Policy Objects (GPOs) to configure Windows Update settings.

**END OF LAB**