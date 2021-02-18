# Practice Lab: Configuring and Managing Permissions and Shares

## Summary

In this lab you will learn how to create folders and manage local and share permissions.

### Scenario

You need to create file shares for the Marketing and IT department to enable users to store their shared files. You have to ensure that only people from the specific departments have access to the files. You decide to create both shares on SEA-CL1 in the E:\\Data folder. The IT department requires that the share and local folder is only accessible to members of the IT group. You advise Bruce Keever and Briana Hernandez to test the file shares and local access to the files.

### Task 1: Create a folder structure

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**.

2. Select the **File Explorer** icon on the taskbar.

3. In File Explorer, in the navigation pane, expand **This PC**, and then select **Allfiles (E:)**. In the details pane, right-click the **empty space**, select **New**, select **Folder**, and then type **Data** for the new folder’s name.

4. In File Explorer, in the navigation pane, expand **Allfiles (E:),** and select **Data**. In the details pane, right-click the empty space, select **New**, select **Folder**, and then type **Marketing** for the new folder’s
    name.

5. In File Explorer, in the details pane, right-click the **empty space**, select **New**, select **Folder**, and then type **IT** for the new folder’s name.

### Task 2: Review default permissions

1. Right-click the **IT** folder, and then select **Properties**.

2. In the IT Properties window, select the **Security tab**, and then select **Edit**.

3. In the Permissions for IT dialog box, verify that Authenticated Users is selected in the Group or user names section, and then select **Remove**. Read the text in the Windows Security dialog box that appears, which explains why you cannot remove an Authenticated Users. select **OK**, and then select **Cancel**.

4. In the IT Properties window, on the Security tab, select **Advanced**.

5. In the Advanced Security Settings for IT dialog box, verify that all permissions entries are inherited from E:\\. Also, verify that Users (SEA-CL1\\Users) have Read & execute access, while Authenticated Users have Modify access. Select **OK** twice.

### Task 3: Configure permissions for the IT and Marketing folders

1. On SEA-CL1, in File Explorer, right-click the **IT** folder, select **Give access to**, and then select **Specific people**.

2. In the Type a name and then select Add, or select the arrow to find someone text box, type **IT**, and then select **Add**.

3. Verify that IT is added and selected. In the Permission Level column, select **Read/Write**, select **Share**, and then select **Done**.

4. Right-click **Marketing**, and then select **Properties**.

5. In the Marketing Properties dialog box, select the **Sharing tab**. In the Network File and Folder Sharing section, verify that Marketing is not shared.

6. In the Advanced Sharing section, Select **Advanced Sharing**.

7. In the Advanced Sharing dialog box, select the **Share this folder** check box. Verify that the share name is Marketing (the same as the folder name), and that Limit the number of simultaneous users to is set to 20.
8. Select **Permissions**.

9. In the Permissions for Marketing dialog box, select the **Everyone** group and select **Remove**.

10. Select **Add**, in the Enter the object names to select (examples) box, type **Marketing**, and then select **OK**. In the Permissions for Marketing section, select the **Change** check box in the Allow column, and then select **OK** twice.

11. In the Marketing Properties dialog box, in the Network File and Folder Sharing section, verify that Marketing is now shared as \\\\LON-CL1\\Marketing, and then select **Close**.

12. Select **Start**, type **cmd** and then select **Command Prompt**.

13. At the command prompt, type the following command, and then press **Enter**.

    ```powershell
    net view \\sea-cl1
    ```

    _**Note**: This will show you all shares created on SEA-CL1_

14. Close the command prompt.

15. Right-click **Start**, and then select **Computer Management**.

16. In Computer Management, in the navigation pane, expand **Shared Folders**, and then select **Shares**. In the details pane, verify that you see IT and Marketing shares, and the default Windows 10 administrative shares.

17. Close Computer Management.

### Task 4: Review configured permissions

1. On SEA-CL1, in File Explorer, right-click **IT**, and then select **Properties**.

2. In the IT Properties window, select the **Security** tab, and then select **Advanced**.

3. In the Advanced Security Settings for IT dialog box, verify that all the permissions entries are set explicitly at this level, because their permission inheritance is set to None.

4. Verify that only the Administrator, Administrators (SEA-CL1\\Administrators) group, SYSTEM and IT (Contoso\\IT) group have access to the IT folder. These settings match the permissions that you configured in the File Sharing dialog box.

5. In the Advanced Security Settings for IT dialog box, select **OK**.

6. In the IT Properties dialog box, select the **Sharing** tab, in the Network File and Folder Sharing section, verify that IT now is shared as \\\\Sea-cl1\\it, and then select **Advanced Sharing**.

7. In the Advanced Sharing dialog box, select **Permissions**. In the Permissions for IT dialog box, verify that the Everyone and Administrators groups have Full Control permissions to the share, select **OK** twice, and then select **Close**.

     _**Note**: If you share a folder by using the File Sharing dialog box, you will modify the local file permissions to match your configuration, while the Everyone and Administrators groups will have the Full Control share permission._

8. In File Explorer, right-click **Marketing**, and then select **Properties**.

9. In the Marketing Properties window, select the **Security tab**, and then select **Advanced**.

10. In the Advanced Security Settings for Marketing dialog box, verify that all of the permissions entries are inherited from E:\\. Also verify that Users (SEA-CL1\\Users) have Read & execute access, while Authenticated Users have Modify access, which are the same file permissions as before you shared the
    Marketing folder. Select **OK** twice.

    _**Note**: If you share a folder by using the Advanced Sharing feature, this does not modify local file permissions. You only modify share permissions if you use Advanced Sharing._

11. Sign out of **SEA-CL1**.

### Task 5: Test local file permissions

1. Sign in to **SEA-CL1** as **Contoso\\Bruce** with the password **Pa55w.rd**.

    _**Note**: Bruce is a member of the Marketing group, but is not a member of the IT group._

2. Select the **File Explorer** icon on the taskbar.

3. In File Explorer, in the navigation pane, expand **This PC**, expand **AllFiles (E:)**, expand **Data**, and then select **Marketing**.

4. In the details pane, right-click the empty space, select **New**, select **Text Document**, and then type **File10** as the name of the file.

    _**Note**: Bruce has local file permissions to create a new file in the Marketing folder, because permissions were configured by using the Advanced Sharing feature. This modified only the share permissions, while the default local file permissions were not modified. By default, Authenticated Users have the Modify permission._

5. In File Explorer, in the navigation pane, select **IT**, and then select **Cancel**.

    _**Note**: You will get an error, because Bruce does not have local file permissions to the IT folder. Permissions were configured by File Sharing, and only members of the IT group have local file permissions to the folder._

6. Sign out of **SEA-CL1**.

7. Sign in to **SEA-CL1** as **Contoso\\Briana** with the password **Pa55w.rd**.

    _**Note**: Briana is member of the IT group, and she is not member of the Marketing group._

8. Select the **File Explorer** icon on the taskbar.

9. In File Explorer, in the navigation pane, expand **This PC**, expand **AllFiles (E:)**, expand **Data**, and then select **Marketing**.

10. In the details pane, verify that you can see File10 that was created by Bruce.

11. Right-click the empty space, select **New**, select **Text Document**, and then type **File20** as the name of the file.

    _**Note**: Briana has local file permissions to create a new file in the Marketing folder because you configured permissions by using the Advanced Sharing feature. This modified only the share permissions, while the default local file permissions were not modified. By default, Authenticated Users have the Modify permission._

12. In File Explorer, in the navigation pane, select **IT**. In the details pane, right-click the empty space, select **New**, select **Text Document**, and then type **File21** as the name of the file.

    _**Note**: Briana is able to create a file, because you configured permissions by using File Sharing. Members of the IT group have local file permissions to the IT folder._

    _**Note**: Be aware that Network File and Folder Sharing modifies file permissions and share permissions. However, the Advanced Sharing feature does not modify file permissions, and only sets share permissions._

13. Sign out of **SEA-CL1**.

### Task 6: Test share permissions

1. Switch to **SEA-CL2**.

2. Sign in to **SEA-CL2** as **Contoso\\Bruce** with the password **Pa55w.rd**.

    _**Note**: Bruce is a member of the Marketing group, but he is not a member of the IT group._

3. Select the **File Explorer** icon on the taskbar.

4. In File Explorer, type **\\\\SEA-CL1** in the Address bar, and then press **Enter**.

5. Verify that you can see the IT and Marketing shares in the details pane.

6. Double-click **Marketing**. Verify that you can see the files that Bruce and Briana created locally.

7. In the details pane, right-click the empty space, select **New**, select **Text Document**, and then type **File30** as the name of the file. Bruce has permissions to create a new file in the Marketing share because he is a member of the Marketing group.

8. In File Explorer, select **SEA-CL1** in the address bar. In the details pane, double-click **IT**. Read the text in the Network Error dialog box, and then select **Close**.

    _**Note**: Bruce is not a member of the IT group, so he does not have permissions to the IT share._

9. Sign out of **SEA-CL2**.

10. Sign in to **SEA-CL2** as **Contoso\\Briana** with the password **Pa55w.rd**.

    _**Note**: Briana is a member of the IT group, but she is not a member of the Marketing group._

11. Select the **File Explorer** icon on the taskbar.

12. In File Explorer, type **\\\\SEA-CL1** in the Address bar, and then press **Enter**.

13. Verify that you can see the IT and Marketing shares in the details pane.

14. Double-click **Marketing**.

15. Read the text in the Network Error dialog box.

    _**Note**: Briana is not a member of the Marketing group, so she does not have permissions to the Marketing share._

16. Select **Close**.

17. In the details pane, double-click **IT**. Right-click the empty space in the details pane, select **New**, select **Text Document**, and then type **File40** as the name of the file.

    _**Note**: Briana has permissions to create a new file in the IT share because she is a member of the IT group. Users can connect only to shares that were shared for groups in which they are members, regardless of whether they were shared by File Sharing or Advanced Sharing._

18. Sign out of **SEA-CL2**.

**Results**: After completing this exercise, you will have created a folder structure for the Marketing and information technology (IT) departments, shared their folders, and tested local and share permissions.

**END OF LAB**