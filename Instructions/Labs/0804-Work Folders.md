# Practice Lab: Work Folders

## Summary

In this lab you will learn how to configure Work Folders as a method of
accessing userfiles from multiple devices.

### Scenario

As marketing users are very often using several devices for their work you want
to provide them with central access to their files by implementing Work Folders.
This allows you to have their files centrally stored. First you will install and
configure the Work Folders on LON-DC1 storing the content in the directory
C:\\syncshare1. To enable the Work Folders for all marketing user you configure
a GPO pointing them to <https://lon-dc1.adatum.com>. Afterwards you test with
Anthony Lynch on his devices LON-CL1 and LON-CL3 how the synchronization is
running and synchronization conflicts are handled.

### Task 1: Install and Configure Work Folders

1. Sign in to **LON-DC1** as **Adatum\\Administrator** with the password
    **Pa55w.rd.**

1. Right-click **Start**, and then select **Windows PowerShell (Admin)**.

1. In Windows PowerShell, type the following cmdlet, and then press **Enter**:

    ```pwsh
    Install-WindowsFeature FS-SyncShareService
    ```

    _**Note**: After the feature installs, you might see a warning display, because Windows automatic updating is not enabled. For the purposes of this lab, ignore the warning._

1. Close the **Windows PowerShell** window.

1. In Server Manager, in the navigation pane, select **File and Storage
    Services**, and then select **Work Folders**.

1. In the **WORK FOLDERS** section, select **TASKS**, and then select **New
    Sync Share**.

1. In the **New Sync Share Wizard**, on the **Before you begin** page, select
    **Next**.

1. On the **Select the server and path** page, in the **Enter a local path**
    text box, type **C:\\syncshare1**, select **Next**

    _**Important:** If **LON-DC1** is not listed in the **Servers** section, select
    **Cancel**. In Server Manager, select **Refresh**, and then repeat this task,
    beginning with step 5 and completing the remaining steps. This may take a
    few minutes for LON-DC1 to show._

1. In the New Sync Share Wizard dialog select **OK**.

1. On the **Specify the structure for user folders** page, verify that **User
    alias** is selected, and then select **Next**.

1. On the **Enter the sync share name** page, select **Next** to accept the
    default sync share name.

1. On the **Grant sync access to groups** page, select **Add**, and in the
    **Enter the object name to select** text box, type **Marketing**. select
    **OK**, and then select **Next**.

1. On the **Specify security policies for PCs** page, verify the two available
    options. Clear the **Automatically lock screen, and require a password**
    check box, and then select **Next**.

1. On the **Confirm selections** page, select **Create**.

1. On the **View Results** page, select **Close**.

1. In Server Manager, in the **WORK FOLDERS** section, verify that
    **syncshare1** is listed, and that in the **USERS** section, the user
    **Anthony Lynch** is listed.

1. On **LON-DC1**, in Server Manager, select **Tools**, and then select
    **Internet Information Services (IIS) Manager**.

1. In the Microsoft Internet Information Services (IIS) Manager, in the
    navigation pane, expand **LON-DC1 (ADATUM\\Administrator)**. If a popup
    window appears, select **No**. Expand **Sites**, right-click **Default Web
    Site**, and then select **Edit Bindings**.

1. In the **Site Bindings** dialog box, select **Add**.

1. In the **Add Site Binding** dialog box, in the **Type** box, select
    **https**. In the **SSL certificate** box, select **LON-DC1.Adatum.com**,
    select **OK**, and then select **Close**.

1. Close the IIS Manager.

### Task 2: Create a GPO to deploy the Work Folders

1. On **LON-DC1**, in Server Manager, select **Tools,** and then select **Group
    Policy Management**.

1. In the Group Policy Management Console, in the navigation pane, expand
    **Forest: Adatum.com**, expand **Domains**, expand **Adatum.com**, and then
    select the **Marketing** organizational unit (OU). 

1. Right-click **Marketing**, and then select **Create a GPO in this domain,
    and Link it here**. In the **Name** text box, type **Deploy Work Folders**,
    and then select **OK**.

1. Right-click **Deploy Work Folders**, and then select **Edit**.

1. In the Group Policy Management Editor, in the navigation pane expand **User
    Configuration**,  expand **Policies**, expand **Administrative Templates**,
    expand **Windows Components**, and then select **Work Folders**.

1. In the details pane, right-click **Specify Work Folder settings**, and then
    select **Edit**.

1. In the **Specify Work Folder settings** dialog box, select **Enabled**. In
    the **Work Folders URL** text box, type <https://lon-dc1.adatum.com>, select
    the **Force automatic setup** check box, and then select **OK**.

1. Close the Group Policy Management Editor.

### Task 3: Test the work folders

1. Switch to **LON-CL1**.

1. Sign in to **LON-CL1** as **Adatum\\anthony** with the password
    **Pa55w.rd**.

1. Select the **File Explorer** icon on the taskbar.

1. In the navigation pane, select **Work Folders**.

1. In the details pane right-click the empty space, select **New**, select
    **Text Document**, and then name the file **On LON-CL1**.

1. Select **Start**, type **Work folders** and select **Manage Work Folders**.

1. On the Manage Work Folders page, check the option **Sync files over metered
    connections**.

    _**Note**: This is only needed due to the hosted lab environment
    configuration._

1. Close the Manage Work Folders window.

1. Switch to **LON-CL3**.

1. Sign in to **LON-CL3** as **LON-CL3\\Admin** with the password **Pa55w.rd**.

1. On **LON-CL3** select **Start**, type
    `\\\\lon-dc1\\certenroll`, and then press **Enter**.

1. In the **Enter Network credentials** dialog box, enter the username as
    **administrator\@adatum.com** and the password as **Pa55w.rd**. Select
    **OK**.

1. In the **certenroll** window, double-click
    **LON-DC1.Adatum.com_AdatumCA.crt.**

1. On the **Certificate dialog** box, select **Install Certificate**.

1. On the **Certificate Import Wizard**, select **Local Machine** and select
    **Next**.

1. On the **User Account Control** dialog box, select **Yes**.

1. On the **Certificate Store** page, select **Place all certificates in the
    following store**, and then select **Browse**.

1. On the **Select Certificate Store** page, select **Trusted Root
    Certification Authorities** and select **OK**.

1. On the **Certificate Store** page, select **Next**.

1. On the **Certificate Import Wizard** page, select **Finish**.

1. In the **Certificate Import Wizard** dialog select **OK**, and then in the
    **Certificate** window, select **OK**.

1. Restart **LON-CL3**.

1. Sign in to **LON-CL3** as **LON-CL3\\Admin** with the password **Pa55w.rd**.

1. On **LON-CL3**, select **Start**, type **Control Panel**, and then press
    Enter.

1. In Control Panel, select **System and Security,** and then select **Work
    Folders**.

1. On the **Manage Work Folders** page, select **Set up Work Folders**.

1. On the **Enter your work email address** page, select **Enter a Work Folders
    URL instead**.

1. On the **Enter a Work Folders URL** page, in the **Work Folders URL** text
    box, type <https://lon-dc1.adatum.com>, and then select **Next**.

1. In the **Windows Security** dialog box, in the **User name** text box, type
    **adatum\\anthony**, and in the **Password** text box, type **Pa55w.rd**,
    and then select **OK**.

1. On the **Introducing Work Folders** page, review the local Work Folders
    location, and then select **Next**.

1. On the **Security policies** page, select the **I accept these policies on
    my PC** check box, and then select **Set up Work Folders**.

1. On the **Work Folders has started syncing with this PC** page, select
    **Close**.

1. Switch to the Manage Work Folders window.

1. On the Manage Work Folders window, check the option **Sync files over
    metered connections**.

    _**Note**: This is only needed due to the hosted lab environment
   configuration._

1. Switch to the Work Folders File Explorer window.

1. Verify that the **On LON-CL1.txt** file displays.

1. Right-click in the details pane, select **New**, select **Text Document**,
    and then in the **Name** text box, type **On LON-CL3**, and then press
    **Enter**.

### Task 4: Test conflict handling

1. Switch to **LON-CL1**.

1. On **LON-CL1**, in **Work Folders**, verify that that both files, **On
    LON-CL1** and **On LON-CL3**, display.

1. Select the **Network** icon in the notification area, and then select
    **Network & Internet settings**.

1. In **Network Status,** select **Change Adapter Options**.

1. Right-click **Ethernet**, and then select **Disable**. In the **User Account
    Control** dialog box, in the **User name** text box, type **Administrator**.
    In the **Password** text box, type **Pa55w.rd**, and then select **Yes**.

1. In **Work Folders**, double-click the **On LON-CL1** file.

1. In Notepad, type **Modified offline**, press Ctrl+S, and then close
    Notepad.

1. In **Work Folders**, right-click in the details pane, select **New**, select
    **Text Document**, and then name the file **Offline LON-CL1**.

1. Switch to **LON-CL3.**

1. On **LON-CL3**, in **Work Folders**, double-click the **On LON-CL1.txt**
    file.

1. In Notepad, type **Online modification,** press Ctrl+S, and then close
    Notepad.

1. Switch to **LON-CL1.**

1. On **LON-CL1**, in the **Network Connections** window, right-click
    **Ethernet**, and then select **Enable**.

1. In the **User Account Control** dialog box, in the **Username** text box,
    type **Administrator**, and in the **Password** text box, type **Pa55w.rd**,
    and then select **Yes**.

1. Switch to **Work Folders**, and then verify that files display in the
    details pane, including **On LON-CL1** and **On LON-CL1-LON-CL1**.

    _Note: Because you modified the file at two locations, a conflict
    occurred, and one of the copies was renamed._

1. Sign out from **LON-CL1** and **LON-CL3**.

**Results**: After finishing this lab you have installed and configured Work
Folders.

## END OF LAB
