# Practice Lab: Configuring Windows Defender

## Summary

In this exercise you will learn how to configure Windows Defender.

### Scenario

You've been asked to test if Windows Defender is properly working on LON-CL3. You've decided to simulate a virus using a special test file, sample.txt, located in \\\\LON-DC1\\labfiles\\Threat folder, to see if it will be properly detected as a virus.

### Task 1: Perform a quick scan

1. Sign in to **LON-CL3** as **Adatum\\Administrator** with the password **Pa55w.rd**.

1. On **LON-CL3** select **Start**, and then select the **Settings** icon.

1. In the Settings app, select **Update & Security**, and then select the **Windows Security** tab.

1. Select **Open Windows Security**.

1. In Windows Security, select **Virus & threat protection**.

1. On the Virus & threat protection page, select **Quick scan**.

1. Close all open windows.

### Task 2: Introduce suspicious software

1. Select the **File Explorer** icon on the taskbar.

1. In **File Explorer** browse to **\\\\LON-DC1\\labfiles**.

1. Copy the **Threat** folder into the E:\\Labfiles folder on LON-CL3.

1. In the Threat folder on LON-CL3, double-click **sample.txt**.  

    _**Note**: The sample.txt file contains a text string to test malware detection._

1. In the sample.txt file, **delete both instances of \<remove\>,** including
    the brackets and any extra lines or blank spaces.

1. Select **Save** and close Notepad.

    _**Note**: Windows Defender will immediately detect a potential threat._

### Task 3: View the quarantined file

1. In the notification area, select the **Notifications** icon, and then in the Action
    Center, select the notification that states that **Threat found**.

     _**Note**: This will open the **Full history** page in Windows security. The file is quarantined now._

. Switch to the file explorer window

    _**Note**: The sample.txt file is now gone from the Threat folder._

1. Close all open windows.

**Results**: After completing this exercise, you should have configured and tested
Windows Defender.

## END OF LAB
