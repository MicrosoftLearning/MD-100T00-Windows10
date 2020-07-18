# Practice Lab: Configuring Internet Explorer Enterprise Mode 

## Summary
In this lab you will learn how to configure the Internet Explorer Enterprise Mode.

_Dependency Notice: The lab requires that a DNS entry for intranet.adatum.com be added, as instructed in the lab_ Configuring and Testing Name Resolution. _If this lab was skipped, complete Task 5 from that lab before continuing._

### Scenario
Adatum is using a web based application for travel requests located at intranet.adatum.com. This application is currently only properly working in older Internet Explorer versions. As you recently upgraded all devices to Windows 10 you must ensure that this web site is still working with IE 11.


### Task 1: Verify the site is not displayed in Enterprise Mode
1.  Sign in to **LON-CL1** as **Adatum\\Harry** with the password **Pa55w.rd**.

2.  Select **Start**, and in the list of apps, expand **Windows
    Accessories**, and then select **Internet Explorer.**

3.  In the Internet Explorer 11 window, select **Use recommended security and compatibility settings**, and then select **OK**.

4.  In the Internet Explorer Address bar, type **http://intranet.adatum.com**,
    and then press **Enter**.

5.  Verify that the website displays correctly.

6.  Press the **ALT** key, select the **Tools menu**, and then verify that the Enterprise Mode menu item is not visible.

7.  Sign out of **LON-CL1**.

### Task 2: Create a policy for Internet Explorer Enterprise Mode
1.  Switch to **LON-DC1**.

2.  Sign in to **LON-DC1** as **Adatum\\Administrator** with the password **Pa55w.rd**.

3.  Select the **File Explorer** icon on the taskbar.

4.  In File Explorer, browse to **E:\\LabFiles\\Apps**.

5.  Double-click the **EMIESiteListManager.msi** file.

6.  In the Enterprise Mode Site List Manager Setup window, select **Next**.

7.  On the End-User License Agreement page, select the check box for **I accept
    the terms in the License Agreement**, and then select **Next**.

8.  On the Destination Folder page, select **Next**.

9.  On the Ready to install Enterprise Mode Site List Manager page, select
    **Install**.

10.  On the Completed the Enterprise Mode Site List Manager Setup Wizard page,
    select **Finish**.

11. Select the **Start** button, type **Enterprise**, then right-click **Enterprise
    Mode Site List Manager** and select **Run as administrator**.

12. In the Enterprise Mode Site List Manager for Windows 10 window, select
    **Add**.

13. In the Add new website window, in the URL text box, type
    **intranet.adatum.com**. In the Compat Mode drop-down list box, select **IE9
    Document Mode**, and then select **Save**.

14. If a dialog box opens, select **Yes**.

15. Select the **File menu**, and then select **Save to XML**.

16. In the Save as… dialog box, navigate to **c:\\inetpub\\wwwroot**. In the
    File name text box, type **AdatumEnterpriseMode**, and then select **Save**.

17. **Close** Enterprise Mode Site List Manager.

18. Select **Start**, and in the list of apps, expand **Windows
    Accessories**, and then select **Internet Explorer**.

19. In the Internet Explorer window, in the Address bar, type  
    **http://lon-dc1.adatum.com/AdatumEnterpriseMode.xml**, and then press
    **Enter**.

20. Verify that the XML file opens correctly.

21. Close Internet Explorer.

### Task 3: Enable Internet Explorer Enterprise Mode  

1.  Switch to the **Server Manager** window, select **Tools**, and then select
    **Group Policy Management**.

2.  In the Group Policy Management window, expand **Forest:
    Adatum.com**, expand **Domains**, expand **Adatum.com**, and select **Group
    Policy Objects**.

3.  Right-click **Group Policy Objects**, and then select **New**.

4.  In the New GPO dialog box, in the Name box, type **Internet Explorer Enterprise Mode Policy**,
    and then select **OK**.

5.  Right-click **Internet Explorer Enterprise Mode Policy**, and then select
    **Edit**.

6.  In the Group Policy Management Editor window, in the left pane, expand
    **Computer Configuration**, expand **Policies**, expand **Administrative
    Templates**, expand **Windows Components**, and then select **Internet
    Explorer**.

7.  Notice that the **Let users turn on and use Enterprise Mode from the Tools
    menu** setting is not configured.

8.  Leave the Group Policy Management Editor window open.

9.  Switch to the **File Explorer** window.

10. In the **File Explorer** window, in the address bar, type **C:\\Windows**, and
    then press **Enter**.

11. In the content pane, right-click the **PolicyDefinitions** folder, and then select
    **Copy**.

12. In the address bar, type **C:\\windows\\SYSVOL\\sysvol\\Adatum.com\\Policies**, and
    then press **Enter**.

13. In the content pane, right-click **any empty space**, and then select
    **Paste**.

14. In the Destination Folder Access Denied dialog select **Continue**.

15. Switch to **LON-CL1**.

16. Sign in to LON-CL1 as **Adatum\\Administrator** with the password **Pa55w.rd**.

17. Select **Start**, and type **cmd**, and press **Enter**.

18. In the Command Prompt window, type the following two commands, press
    **Enter** after each command, and press **Y** and **Enter** when asked to
    overwrite the files:    
``` 
Copy C:\Windows\PolicyDefinitions\inetres.admx \\LON-DC1\SYSVOL\Adatum.com\Policies\PolicyDefinitions\inetres.admx
```
```
Copy C:\Windows\PolicyDefinitions\en-US\inetres.adml \\\ON-DC1\SYSVOL\Adatum.com\Policies\PolicyDefinitions\en-US\inetres.adml
```

19.  Sign out of **LON-CL1**.

19.  Switch to **LON-DC1**.

20.  On LON-DC1, switch to **Group Policy Management Editor** window. You should
     still see the available Internet Explorer policy settings in the content
     pane.

21.  In the content pane, double-click **Let users turn on and use Enterprise Mode from the Tools menu**.

22.  Select **Enabled**, and then select **OK**.

23.  In the content pane, double-click **Use the Enterprise Mode IE website list**.

24.  Select **Enabled**, in the Type the location (URL) of your Enterprise Mode IE
     website list text box, type **http://lon-dc1.adatum.com/AdatumEnterprisemode.xml**, and then select
     **OK**.

25.  Close the Group Policy Management Editor window.

26.  In the Group Policy Management window, right-click the **Adatum.com domain**, and then select **Link an existing GPO**.

27.  In the Select GPO window, select **Internet Explorer Enterprise Mode
     Policy**, and select **OK**.

28. Close the Group Policy Management and File Explorer window

### Task 4: Verify the site is now in enterprise mode

1.  Switch to **LON-CL1**

2.  Sign in to **LON-CL1** as **Adatum\\Harry** with the password **Pa55w.rd**.

3.  Select **Start** and type **cmd**. Press **Enter**.

4.  At the command prompt, type the following command, and then press Enter. 

    `gpupdate /force`

5.  Select **Start**, and in the list of apps, expand **Windows Accessories**, and then select **Internet Explorer**, and then wait two minutes.

6.  In the Internet Explorer window, press the **ALT** key, select the **Tools**
    menu, and then select **Enterprise Mode**.

7.  In the Internet Explorer Address bar, type **http://intranet.adatum.com**,
    and then press **Enter**.

8.  Verify that the website displays correctly, and if you press the **ALT**
    key, select the **Tools** menu, and then verify that Enterprise Mode is
    greyed out because the site runs in Enterprise Mode.

9.  Sign out of **LON-CL1**.

**Results**: After completing this exercise, you should have successfully configured the Internet Explorer Enterprise Mode.

**END OF LAB**