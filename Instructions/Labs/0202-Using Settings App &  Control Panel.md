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

1.  Sign in to LON-CL3 as **LON-CL3\\Admin** with the password **Pa55w.rd**.

2.  On **LON-CL3** select **Start,** and then select the **Settings** icon.

3.  In the Settings app, select **Update & Security**, and then open the
    **Windows Security** tab.

4.  Select **Virus & threat protection**.

5.  In Virus & threat protection select **manage settings.**

6.  In Virus & threat protection settings, scroll down and then select **Add or
    remove exclusions.**

7.  In Exclusions select **Add an exclusion** and then select **Folder**.

8.  Browse to **C:\\UTIL** and select **Select Folder**. In the User Account
    Control window select **Yes**.

    _Note: C:\\Util is now listed as exclusion._

9. Close the Windows Security app.

10. Close the Settings app.

 

### Task 2: Using Control Panel

1.  Select **Start** and type **Control Panel**. Press **Enter**.

2.  In the Control Panel window select **Hardware and Sound** and then select
    **Power Options**.

3.  Select **Create a power plan.**

4.  Enter "**Power Save - Presentation**" in the Plan Name field and select
    **Next**.

5.  Select **Create**.

6.  Under Preferred Plans, select **Change plan settings** next to the plan you
    created.

7.  Select **Change advanced power settings**.

8.  Scroll down and expand the **Multimedia settings** option.

9.  Expand the **When playing video** option and confirm the setting **Optimize
    Video Quality**.

10. Select **Ok**.

11. Set the Turn off the display to **30 minutes** and select **Save changes**.

12. Close all open windows.

 

**Results:** After finishing the exercise you have excluded one folder from
Virus scanning and you have created a new power plan.

**END OF LAB**