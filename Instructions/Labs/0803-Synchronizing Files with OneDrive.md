# Practice Lab: Synchronizing files with OneDrive

## Summary

In this lab you will learn how to synchronize content between devices using
OneDrive.

_Dependency Note: This lab requires the use of the Microsoft ID created
previously in the Synchronizing Settings lab._

### Scenario

Your organization would like to leverage OneDrive as a method for accessing user
files from any device. You have been tasked with testing creating a file on
LON-CL3 and synchronizing changes between LON-CL1, using your test Microsoft ID.

### Task 1: Enable sync on LON-CL3

1. Sign in to **LON-CL3** as Your first name + Last name’s first
    letter**MD100\@outlook.com** with the password **Pa55w.rd123** or using your
    **PIN**.

1. Select the **File Explorer** icon on the taskbar, and then select the
    **OneDrive** node. If you receive a prompt to sign in, use the *Your first
    name + Last name’s first letter***MD100\@outlook.com** credentials.

    _**Note**: The OneDrive node in File Explorer might take several minutes to
appear. Please wait for it to appear before proceeding. If it takes longer
than 15 minutes, sign out, and then sign back in by using your Microsoft
account._

1. In the File Explorer console tree, expand **OneDrive**, and then select the
    **Documents** folder.

1. Right-click the empty space in the **Details pane**, select **New**, and
    then select **Text Document**.

1. Type **I was here** in the **Name** box, and then press Enter.

1. Double-click the **I was here** document, and when Notepad opens, type **I
    was here on LON-CL3**. Press **Ctrl+S**, and then close Notepad.

1. Wait until OneDrive has synchronized the changes indicated by a green check
    mark symbol in the **Status** row.

    _**Note**: If OneDrive indicates it is paused, right-click on the OneDrive status icon, select Resume Syncing._

### Task 2: Sign in to LON-CL1 with your Microsoft account, and update the synchronized document

1. Switch to **LON-CL1**.

1. Sign in to **LON-CL1** as Your first name + Last name’s first
    letter**MD100\@outlook.com** with the password **Pa55w.rd123** or using your
    **PIN**.

1. Select the **File Explorer** icon on the taskbar, and then select the
    **OneDrive** node.

1. In the **File Explorer** console tree, expand **OneDrive**, and then select
    the **Documents** folder. After a few minutes, the **I was here** document
    should appear (it can take up to five minutes).

    _**Note**: By default, OneDrive has the Files On-Demand feature enabled that will
    download files only on the first use on a device. Such cloud files that have
    been created Online or on another device are indicated by a cloud symbol in
    Status._

1. Double-click the **I was here** document.  

    _**Note**: The file will now be downloaded to your device before it will open. If OneDrive indicates it is paused, right-click on the OneDrive status icon, select Resume Syncing._

1. In the **Notepad** window, directly under the **I was here on LON-CL3**
    line, type **Now I’m here on LON-CL1**, and then press **Enter**.

1. Press **Ctrl+S**, and then close Notepad.

1. Make a note of the date and time of the **I was here.txt** file.

1. Switch to **LON-CL3**.

1. Check the date and time of the **I was here.txt** document. When it changes
    to the date and time you noted on **LON-CL1**, double-click the file (it
    takes up to five minutes to change).

     _**Note**: You should now see two lines in Notepad, as follows:_

    > _I was here on LON-CL3_
    >
    > _Now I’m here on LON-CL1*

1. Close Notepad.

1. Right-click the **I was here** document and select **Always keep on this
    device.**  

     _**Note**: The check mark symbol in Status will now change to a white check mark
    in a green circle indicating that this file is always available on your
    device._

1. Right-click the **I was here** document and select **Free up space.**  

     _**Note**: This will convert the file back to an online document indicated
    by the cloud symbol that needs to be downloaded on the first use. This is
    intended to free up space on your local hard disk._

1. Sign out of **LON-CL1** and **LON-CL3**.

**Results**: During this lab you have synchronized files between different
devices using OneDrive.

## END OF LAB
