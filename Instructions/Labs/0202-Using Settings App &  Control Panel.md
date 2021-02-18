# Practice Lab: Using the Settings App and Control Panel

## Summary

In this lab you will learn how to modify computer settings using the Windows 10
Settings App and the Control Panel.

### Scenario

You need to use the Settings app to ensure that the antivirus program does not
scan the Util folder on drive (C:), because it contains some scripts that
deliberately trigger and test antivirus programs. Additionally, you will need to
create a new power plan that minimizes power usage, but does not impact sales
staff playing the presentations while on battery.

### Task 1: Using the Settings Apps

1. Sign in to LON-CL3 as **LON-CL3\\Admin** with the password **Pa55w.rd**.

1. On **LON-CL3** select **Start,** and then select the **Settings** icon.

1. In the Settings app, select **Update & Security**, and then open the
    **Windows Security** tab.

1. Select **Virus & threat protection**.

1. In Virus & threat protection select **manage settings.**

1. In Virus & threat protection settings, scroll down and then select **Add or
    remove exclusions.**

1. In Exclusions select **Add an exclusion** and then select **Folder**.

1. Browse to **C:\\UTIL** and select **Select Folder**. In the User Account
    Control window select **Yes**.

    _Note: C:\\Util is now listed as exclusion._

1. Close the Windows Security app.

1. Close the Settings app.

### Task 2: Using Control Panel

1. Select **Start** and type **Control Panel**. Press **Enter**.

1. In the Control Panel window select **Hardware and Sound** and then select
    **Power Options**.

1. Select **Create a power plan.**

1. Enter "**Power Save - Presentation**" in the Plan Name field and select
    **Next**.

1. Select **Create**.

1. Under Preferred Plans, select **Change plan settings** next to the plan you
    created.

1. Select **Change advanced power settings**.

1. Scroll down and expand the **Multimedia settings** option.

1. Expand the **When playing video** option and confirm the setting **Optimize
    Video Quality**.

1. Select **Ok**.

1. Set the Turn off the display to **30 minutes** and select **Save changes**.

1. Close all open windows.

**Results:** After finishing the exercise you have excluded one folder from
Virus scanning and you have created a new power plan.

## END OF LAB
