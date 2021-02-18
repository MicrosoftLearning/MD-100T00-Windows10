# Practice Lab: Using File History to Recover Files

## Summary

In this exercise you will learn how configure File History and use it to restore previous versions of a file or folder. 

## Exercise 1: Configure File History

### Scenario

You need to ensure that users can recover deleted files stored in the Documents library on their local workstations. You decide to validate the File History feature using SEA-CL2. You will create a shared folder on SEA-SVR1 named FileHistory that will be used as a central location to store file history data.  

### Task 1: Create a shared folder for File History

1. Sign in to **SEA-SVR1** as **Contoso\\Administrator** with the password **Pa55w.rd**.
2. Select the **File Explorer** icon on the taskbar and in the navigation pane, select **Local Disk (C:)**.
3. In File Explorer, in the details pane, right-click an empty space, point to **New**, and then select **Folder**. Type **FileHistory** as the folder name, and then press Enter.
4. Right-click the **FileHistory** folder, and then select **Properties**.
5. In the **FileHistory Properties** dialog box, on the **Security** tab, select **Edit**. Select **Add**, in the **Enter the object names to select** box, type **Domain**, and then select **OK**.
6. Select **Domain Users**, and then select **OK**.
7. In the **Permissions for Domain Users** section, in the Allow column, select the **Full control** check box, and then select **OK**.
8. On the **Sharing** tab, select **Advanced Sharing**.
9. Select the **Share this folder** check box, and then select **Permissions**. In the **Permissions for Everyone** section, in the Allow column, select **Full Control**, and then select **OK** twice.
10. In the **FileHistory Properties** dialog box, select **Close**.
11. Close File Explorer.
12. Sign out of SEA-SVR1.

### Task 2: Configure and test File History

1. Switch to **SEA-CL2** and sign in as **Contoso\\Administrator**, with the password **Pa55w.rd**.
2. On **SEA-CL2**, on the taskbar, select the **File Explorer** icon.
3. In File Explorer, in the navigation pane, expand **This PC**, and then select **Documents**. In the details pane, right-click an empty space, point to **New**, select **Text Document**, and then enter **Report** as the name of the file.
4. Double-click **Report.txt**, and in Notepad, type **This is a report**. Close the Notepad file, and then select **Save** to save the changes.
5. Select Start, type **file history**, and then select **Restore your files with File History**.
6. In the **Home – File History** window, select **Configure File History settings**.
7. In the **File History** window, in the navigation pane, select **Select drive**.
8. In the **Select Drive** dialog box, select **Add network location**.
9. In the **Folder** box, type **\\\\SEA-SVR1\\FileHistory**, select **Select Folder**, and then select **OK**.
10. In the **File History** window, in the details pane, select **Turn on**.
11. In the navigation pane, select **Advanced settings**, review the default values for how often to save copies of files and how long to keep saved versions, and then select **Cancel**.
12. In File Explorer, in the navigation pane, select **Documents**, right-click **Report.txt**, and then select **Delete**.
13. In File Explorer, select the **Home** tab, and then select **History**.
14. In the Documents – File History window, right-click **Report.txt**, and select **Preview**. Confirm that you can see the text **This is a report**, and then select the round button with the arrow to restore the file to the original location.
15. File Explorer opens. Verify that Report.txt has been recovered to the original location. Double-click **Report.txt**, confirm that it contains the text that you typed, close Notepad, and then close File Explorer.
16. In the Report.txt – File History window, on the left of the address box, select the upward-pointing arrow twice.
17. Review the folders and libraries that File History is protecting, and confirm that the a folder named Data and a folder named Reports are not among them.
18. Close the Home – File History window.

**Results**: After completing this exercise, you will have successfully configured File History and validated a successful recovery of a protected file.

## Exercise 2: Protect Additional Data

### Scenario

An additional request has been made to protect specific files being added to SEA-CL2. A script has been provided named CopyUserData.bat to be used to create the intended folders and copy the required data. The *Data* folder needs to be added to the document library, but both the *Data* and *Reports* folder must both be protected by File History.

### Task 1: Run the CopyUserData script

1. On **SEA-CL2**, in File Explorer, browse to **\\\\SEA-DC1\\labfiles\\Support\\**.

2. In the content pane, double-click **CopyUserData** to copy lab files to the local client.

3. In File Explorer, in the navigation pane, expand **Local Disk (C:)**, and then select **Data**. In the details pane, right-click **Sales.txt**, select **Properties**, select the **Previous Versions** tab, confirm that there are no previous versions available, and then select **OK**. 

### Task 2: Configure Additional Folders

1. In the navigation pane, right-click **Data**, select **Include in library**, and then select **Documents**. As File History protects the Documents library, File History is now also protecting the Data folder.

2. In File Explorer, in the navigation pane, select **Reports**. In the details pane, right-click **Report.txt**, select **Properties**, select the **Previous Versions** tab, confirm that there are no previous versions available, and then select **OK**.

3. On the taskbar, in the **Type here to search** box, enter **file history**, and then select **Backup settings**.

4. In the **Settings** window, in the **Back up using File History** section, select **More options**.

5. On the **Backup options** page, in the **Back up these folders** section, select **Add a folder**, in the **Folder** box, type **C:\\Reports**, select **Choose this folder**, and then close the **Settings** window.

6. In the **File History** window**,** in the **File History is on** section, select **Run now**.

7. In File Explorer, in the details pane, right-click **Report.txt**, select **Properties**, select the **Previous Versions** tab, verify that there is now one previous version, and then select **OK**.

8. In the navigation pane, right-click **Data**, select **Properties**, select the **Previous Versions** tab, and then select **Data** in the **Folder versions** section.

9. Select the arrow near the **Restore** button, and then verify that you can restore the previous version either to the original location or to a custom location.

10. In the **Data Properties** dialog box, select the arrow near the **Open** button, and then select **Open in File History**.

11. In the Data – File History window, on the left of the address box, select the upward-pointing arrow once. Notice that File History is protecting the Data and Reports folders, in addition to the Users folder, which is protected by default.

12. In the C:\\ - File History window, select the upward-pointing arrow again to view all folders and libraries that File History is protecting.

13. Close the Home – File History window, in the **Data Properties** dialog box, select **OK**.

14. Close all open windows and sign out of SEA-CL2.

**Results**: After completing this exercise, you will have successfully added additional files to be protected by using File History.

**END OF LAB**