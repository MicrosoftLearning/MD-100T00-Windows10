# Practice Lab: Using File History to Recover Files

## Summary

In this exercise you will learn how configure File History and use to restore
previous versions of a file.

## Exercise 1: Configure File History

### Scenario

You have been asked to ensure users can recover deleted files in the Documents
library on LON-CL3 using File History, with the FileHistory shared folder on
LON-DC1. The solution needs to be tested.

### Task 1: Create a shared folder for File History

1. Sign in to **LON-DC1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

1. On **LON-DC1**, select the **File Explorer** icon on the taskbar. In the
    navigation pane, select **AllFiles (E:)**.

1. In File Explorer, in the details pane, right-click an empty space, point to
    **New**, and then select **Folder**. Type **FileHistory** as the folder
    name, and then press Enter.

1. Right-click the **FileHistory** folder, and then select **Properties**.

1. In the **FileHistory Properties** dialog box, on the **Security** tab,
    select **Edit**. Select **Add**, in the **Enter the object names to select**
    box, type **Domain**, and then select **OK**.

1. Select **Domain Users**, and then select **OK**.

1. In the **Permissions for Domain Users** section, in the Allow column, select
    the **Full control** check box, and then select **OK**.

1. On the **Sharing** tab, select **Advanced Sharing**.

1. Select the **Share this folder** check box, and then select **Permissions**.
    In the **Permissions for Everyone** section, in the Allow column, select
    **Full Control**, and then select **OK** twice.

1. In the **FileHistory Properties** dialog box, select **Close**.

1. Close File Explorer.

### Task 2: Configure and test File History

1. Switch to **LON-CL3**.

1. Sign-in to **LON-CL3** as **Adatum\\Administrator**, with the password
    **Pa55w.rd**.

1. On **LON-CL3**, on the taskbar, select the **File Explorer** icon.

1. In File Explorer, in the navigation pane, expand **This PC**, and then
    select **Documents**. In the details pane, right-click an empty space, point
    to **New**, select **Text Document**, and then enter **Report** as the name
    of the file.

1. Double-click **Report.txt**, and in Notepad, type **This is a report**.
    Close the Notepad file, and then select **Save** to save the changes.

1. On the taskbar, in the **Type here to search** box, type **file history**,
    and then select **Restore your files with File History**.

1. In the **Home – File History** window, select **Configure File History**
    settings.

1. In the **File History** window, in the navigation pane, select **Select
    drive**.

1. In the **Select Drive** dialog box, select **Add network location**.

1. In the **Folder** box, type
    **\\\\LON-DC1\\FileHistory**, select **Select
    Folder**, and then select **OK**.

1. In the **File History** window, in the details pane, select **Turn on**.

1. In the navigation pane, select **Advanced settings**, review the default
    values for how often to save copies of files and how long to keep them, and
    then select **Cancel**.

1. In File Explorer, in the navigation pane, select **Documents**, right-click
    **Report.txt**, and then select **Delete**.

1. In File Explorer, select the **Home** tab, and then select **History**.

1. In the Documents – File History window, right-click **Report.txt**, and
    select **Preview**. Confirm that you can see the text **This is a report**,
    and then select the round button with the arrow to restore the file to the
    original location.

1. File Explorer opens. Verify that Report.txt has been recovered to the
    original location. Double-click **Report.txt**, confirm that it contains the
    text that you typed, close Notepad, and then close File Explorer.

1. In the Report.txt – File History window, on the left of the address box,
    select the upward-pointing arrow twice.

1. Review the folders and libraries that File History is protecting, and
    confirm that the Data folder and Reports folder are not among them. Close
    the Home – File History window.

## Exercise 2: Protect Additional Data

### Scenario

An additional request has been made to protect the additional data being added
on LON-CL3. A script has been provided to copy the data,
\\\\LON-DC1\\labfiles\\Support\\CopyUserData.bat.
The **Data** folder needs to be added to the document library, but both the **Data**
and **Reports** folder must both be protected. It needs to be confirmed that
previous versions of **Reports.txt** are available following a File History
backup.

### Task 1: Run the data copy script

1. On **LON-CL3**, in Windows Explorer, browse to
    **\\\\LON-DC1\\labfiles\\Support\\**.

1. In the content pane, double-click **CopyUserData** to copy lab files to the
    local client.

1. In File Explorer, in the navigation pane, expand **Local Disk (C:)**, and
    then select **Data**. In the details pane, right-click **Sales.txt**, select
    **Properties**, select the **Previous Versions** tab, confirm that there are
    no previous versions available, and then select **OK**.

### Task 2: Configure Additional Folders

1. In the navigation pane, right-click **Data**, select **Include in library**,
    and then select **Documents**. As File History protects the Documents
    library, where you added the folder, File History is now also protecting the
    Data folder.

1. In File Explorer, in the navigation pane, select **Reports**. In the details
    pane, right-click **Report.txt**, select **Properties**, select the
    **Previous Versions** tab, confirm that there are no previous versions
    available, and then select **OK**.

1. On the taskbar, in the **Type here to search** box, enter **file history**,
    and then select **Backup settings**.

1. In the **Settings** window, in the **Back up using File History** section,
    select **More options**.

1. On the **Backup options** page, in the **Back up these folders** section,
    select **Add a folder**, in the **Folder** box, type **C:\\Reports**, select
    **Choose this folder**, and then close the **Settings** window.

1. In the **File History** window**,** in the **File History is on** section,
    select **Run now**.

1. In File Explorer, in the details pane, right-click **Report.txt**, select
    **Properties**, select the **Previous Versions** tab, verify that there is
    now one previous version, and then select **OK**.

1. In the navigation pane, right-click **Data**, select **Properties**, select
    the **Previous Versions** tab, and then select **Data** in the **Folder
    versions** section.

1. Select the arrow near the **Restore** button, and then verify that you can
    restore the previous version either to the original location or to a custom
    location.

1. In the **Data Properties** dialog box, select the arrow near the **Open**
    button, and then select **Open in File History**.

1. In the Data – File History window, on the left of the address box, select
    the upward-pointing arrow once. Notice that File History is protecting the
    Data and Reports folders, in addition to the Users folder, which is
    protected by default.

1. In the C:\\ - File History window, select the upward-pointing arrow again to
    view all folders and libraries that File History is protecting.

1. Close the Home – File History window, in the **Data Properties** dialog box,
    select **OK**, and then close the File History window.

1. Close all open windows

**Results**: After completing this exercise, you will have successfully
configured File History to recover files.

## END OF LAB
