# Practice Lab: Recovering using Driver Rollback

## Summary

In this exercise you will learn how to do a Driver Rollback and Safe Mode to
repair a driver when the system is unusable.

### Scenario

You've been given a new keyboard driver to test on LON-CL1. As there is concern
it may fail, it's recommended to enable Picture password in case the keyboard is
unresponsive. In the even this happens, you'll need to use Safe Mode to correct
the issue.

### Task 1: Configure a picture password as a sign-in option

1. Sign in to **LON-CL1** as **Adatum\\Administrator** with the password of
    **Pa55w.rd**.

1. Select the **Start** icon, and then select **Settings**.

1. In the **Settings** dialog box, select **Accounts**, select **Sign-in
    options**, and then in the **Picture password** section select **Add**. In
    the **Windows Security** dialog box, enter **Pa55w.rd** as the password, and
    then select **OK**.

1. In the Welcome to picture password window, select **Choose picture**, browse
    to **C:\\Windows\\Web\\Screen**, select **img100.jpg**, select **Open**, and
    then select **Use this picture**.

1. Follow the on-screen instructions, and then draw three gestures on the
    picture. Remember which gestures you are using, as you will repeat them
    later to sign in!

1. Repeat the pattern to confirm, select **Finish**, and then close the
    Settings window.

1. Select **Start** and enter **Control** in the Search field.  Select **Control Panel**.

1. Select **Ease of Access**, then select **Ease of Access Center**.  On the left side, select
    **Change sign-in settings**.

1. Check the **At sign-in** box next to the **Type without the keyboard (On-Screen Keyboard)** setting. Select **OK** and close the **Ease of Access Center** window.

1. Select **Start** and type **Local Security** in the search field. Select **Local Security Policy**.

1. In the Local Security Policy window, on the left side, expand Local Policies, and select **Security Options**.

1. In the details view, double-click on the **Interactive Logon: Do not require CTRL+ALT+DEL** option. In the dialog box, select **Enabled** and then select **OK**.

1. Close all windows.

    _**Note**: Due to the restrictions of the lab environment VMs, this process is
    in-place to ensure you are able to continue the lab._

### Task 2: Update a driver in Device Manager

1. In LON-CL1, on the taskbar, right-click the **Start** icon, and then select
    **Device Manager**.

1. In Device Manager, expand **Keyboards**, right-click **Standard PS/2
    Keyboard**, and then select **Properties**.

1. In the **Standard PS/2 Keyboard Properties** dialog box, select the
    **Driver** tab, and then confirm that the **Roll Back Driver** button is not
    available. select **Update Driver**.

1. In the **Update Drivers – Standard PS/2 Keyboard** dialog box, select
    **Browse my computer for driver software**.

1. On the **Browse for drivers on your computer** page, select **Let me pick
    from a list of available drivers on my computer**.

1. On the **Select the device driver you want to install for this hardware**
    page, clear the **Show compatible hardware** check box. In the
    **Manufacturer** section, select **Microsoft**, in the **Model** section,
    select **Microsoft USB Internet Keyboard**, select **Next**, in the **Update
    Driver Warning** box, select **Yes**, and then select **Close** twice.

1. In the **System Settings Change** dialog box, select **Yes**, and then wait
    until the computer restarts.

### Task 3: Roll back a driver using Safe mode

1. Sign in to **LON-CL1** as **Adatum\\Administrator** by repeating the three
    gestures that you defined for the picture password in Task 1.

1. On the taskbar, in the **Type here to search** box, type **notepad**, and
    then press **Enter**.

    _**Note**: If the keyboard is not working, you should skip steps 2, 3, and 7._

1. In Notepad, type your name to confirm that the keyboard is still working.

1. Right-click the **Start** icon, and then select **Device Manager**.

1. In Device Manager, right-click **Microsoft Hyper-V Virtual Keyboard**,
    select **Disable device**, and then select **Yes**.

1. Right-click **Microsoft USB Internet Keyboard**, select **Properties**, and
    then read the device status.

1. In Notepad, try to type your name again. As neither keyboard is operational,
    you cannot use a keyboard in LON-CL1.

1. In the **Microsoft USB Internet Keyboard Properties** dialog box, select the
    **Driver** tab. Confirm that Roll Back Driver is available, and select
    **Cancel**.

1. Close Device Manager.

1. Right-click the **Start** icon, and then select **Computer Management**.

1. In Computer Management, in the navigation pane, expand **Services and
    Applications**, and then select **Services**. In the details pane, select
    the Status column to sort the services, scroll down, and verify that many
    services (more than 75 services) are running, and then close Computer
    Management.

1. Select **Start**, and then select the **Settings** icon.

1. In the Settings app, select **Update & Security**, and then select the
    **Recovery** tab.

1. Under Advanced Startup select **Restart now**.

1. On the Choose an option page select **Troubleshoot**.

1. On the troubleshoot page select **Advanced Options**.

1. On the Advanced options page, select **Startup Settings**, select
    **Restart**.

1. After restarting, press **4** to select **Enable Safe Mode**.

1. When the computer starts, sign in as **Adatum\\Administrator** and use
    **Pa55w.rd** as the password.

    _**Note**: As the keyboard is not working you need to use the onboard keyboard
    to enter the password._

1. Verify that the words Safe Mode appear in all four corners of the desktop.
    Right-click the **Start** icon, and then select **Device Manager**.

1. Right-click **Microsoft USB Internet Keyboard**, select **Properties**,
    select the **Driver** tab, select **Roll Back Driver**, select **Previous
    version of the driver had more features**, and then select **Yes**.

1. Confirm that the **Roll Back Driver** option is no longer available, as
    driver rollback can go back by only one version, and then select **Close**.

1. On the taskbar, in the **Type here to search** box, type **notepad**, and
    then press **Enter**.

1. In Notepad, type your name to confirm that the keyboard is working again,
    and then close Notepad without saving changes.

1. In Device Manager, right-click **Generic PnP Monitor**, select
    **Properties**, and then verify that the status of the device is not
    available when the computer is running in safe mode.

1. Select the **Driver tab** and verify that you can still use the **Update
    Driver or Uninstall Device** options while the computer is running in safe
    mode. Select **OK**.

1. In Device Manager, right-click **Microsoft Hyper-V Virtual Keyboard**,
    select **Enable device**, and then close Device Manager.

1. Right-click the **Start** icon, and then select **Computer Management**.

1. In Computer Management, in the navigation pane, expand **Services and
    Applications**, and then select **Services**. In the details pane, select
    the Status column to sort the services, scroll down, and verify that only a
    few services (less than 25 services) are running when the computer is in
    safe mode.

1. Close Computer Management

1. Restart **LON-CL1**.

### Task 4: Verify if keyboard is working

1. Sign in to **LON-CL1** as **Adatum\\Administrator** with the password of
    **Pa55w.rd**.

1. On the taskbar, in the **Type here to search** box, type **notepad**, and
    then press **Enter**.

1. In Notepad, type your name to confirm that the keyboard is again working.

1. Close Notepad without saving changes.

1. Right-click the **Start** icon, and then select **Device Manager**.

1. Right-click **Standard PS/2 Keyboard**, select **Properties**, and then read
    the device status.

1. Select **OK**.

1. Close all open windows.

**Results**: After completing this exercise, you should have successfully rolled
back a driver and browsed safe mode.

## END OF LAB
