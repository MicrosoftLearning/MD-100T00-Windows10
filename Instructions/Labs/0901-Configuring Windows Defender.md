# Practice Lab: Configuring Windows Defender 

## Summary

In this exercise you will learn how to configure Windows Defender.

### Scenario
You've been asked to test if Windows Defender is properly working on LON-CL3. You've decided to simulate a virus using a special test file, sample.txt, located in \\\\LON-DC1\\labfiles\\Threat folder, to see if it will be properly detect as a virus. 

### Task 1: Perform a quick scan

1.  Sign in to **LON-CL3** as **Adatum\\Administrator** with the password **Pa55w.rd**.

2.  On **LON-CL3** select **Start**, and then select the **Settings** icon.

3.  In the Settings app, select **Update & Security**, and then select the **Windows Security** tab.

4.  Select **Open Windows Security**.

5.  In Windows Security, select **Virus & threat protection**.

6.  On the Virus & threat protection page, select **Quick scan**.

7.  Close all open windows.

### Task 2: Introduce suspicious software

1.  Select the **File Explorer** icon on the taskbar.

2.  In **File Explorer** browse to **\\\\LON-DC1\\labfiles**.

3.  Copy the **Threat** folder into the E:\\Labfiles folder on LON-CL3.

4.  In the Threat folder on LON-CL3, double-click **sample.txt**.  

    _**Note**: The sample.txt file contains a text string to test malware detection._

5.  In the sample.txt file, **delete both instances of \<remove\>,** including
    the brackets and any extra lines or blank spaces.

6.  Select **Save** and close Notepad.

    _**Note**: Windows Defender will immediately detect a potential threat._

### Task 3: View the quarantined file ###
1.  In the notification area, select the **Notifications** icon, and then in the Action
    Center, select the notification that states that **Threat found**.

     _**Note**: This will open the **Full history** page in Windows security. The file is quarantined now._

2.  Switch to the file explorer window

    _**Note**: The sample.txt file is now gone from the Threat folder._

3.  Close all open windows.

**Results**: After completing this exercise, you should have configured and tested
Windows Defender.

**END OF LAB**