# Practice Lab: Configuring and Managing Permissions and Shares

## Summary

In this lab you will learn how to create and manage a shared folder.

### Scenario

Your manager has advised you to create file shares for the Marketing and IT department to enable the users can store their shared files. Nevertheless you have to ensure that only people from the specific departments have access to the files. You decide to create both shares on LON-CL1 in the E:\\Data folder. The IT department requires that the share and local folder is only accessible to members of the IT group. You advise Bill Norman and Beth Burke to test the file shares and local access to the files.

### Task 1: Create a folder structure

1. Sign in to **LON-CL1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**,

1. Select the **File Explorer** icon on the taskbar.

1. In File Explorer, in the navigation pane, expand This PC, and then select
    **Allfiles (E:)**. In the details pane, right-click the **empty space**,
    select **New**, select **Folder**, and then **type Data** for the new
    folder’s name.

1. In File Explorer, in the navigation pane, expand **Allfiles (E:),** and select
    **Data**. In the details pane, right-click the **empty space**, select
    **New**, select **Folder**, and then type **Marketing** for the new folder’s
    name.

1. In File Explorer, in the details pane, right-click the **empty space**,
    select **New**, select **Folder**, and then type **IT** for the new folder’s
    name.

### Task 2: Review default permissions

1. Right-click the **IT** folder, and then select **Properties**.

1. In the IT Properties window, select the **Security tab**, and then select
    **Edit**.
1. In the Permissions for IT dialog box, verify that Authenticated Users is
    selected in the Group or user names section, and then select Remove. Read the
    text in the Windows Security dialog box that appears, which explains why you
    cannot remove an authenticated user. select **OK**, and then select
    **Cancel**.

1. In the IT Properties window, on the Security tab, select **Advanced**.

1. In the Advanced Security Settings for IT dialog box, verify that all
    permissions entries are inherited from E:\\. Also, verify that Users
    (LON-CL1\\Users) have Read & execute Access, while Authenticated Users have
    Modify Access. select OK twice.

### Task 3: Configure permissions for the IT and Marketing folders

1. On LON-CL1, in File Explorer, right-click the **IT folder**, select **Give access to**, and then select **Specific people**.

1. In the Type a name and then select Add, or select the arrow to find
    someone text box, type **IT**, and then select **Add**.

1. Verify that IT is added and selected. In the Permission Level
    column, select **Read/Write**, select **Share**, and then select **Done**.

1. Right-click **Marketing**, and then select **Properties**.

1. In the Marketing Properties dialog box, select the **Sharing tab**. In the
    Network File and Folder Sharing section, verify that Marketing is not
    shared.

1. In the Advanced Sharing section, Select **Advanced Sharing**.

1. In the Advanced Sharing dialog box, select the **Share this folder check
    box**. Verify that the share name is Marketing (the same as the folder
    name), and that Limit the number of simultaneous users to is set to 20.
1. Select **Permissions**.

1. In the Permissions for Marketing dialog box, select the **Everyone** group
    and select **Remove**.

1. Select **Add**, in the Enter the object names to select
    (examples) box, type **Marketing**, and then select **OK**. In the
    Permissions for Marketing section, select the **Change check box** in the
    Allow column, and then select **OK** twice.

1. In the Marketing Properties dialog box, in the Network File and Folder
    Sharing section, verify that Marketing is now shared as
    \\\\LON-CL1\\Marketing, and then select **Close**.

1. Select **Start**, type **cmd** and then select **Command Prompt**.

1. At the command prompt, type the following command, and then press **Enter**.

    ```bat
    net view \\\\lon-cl1
    ```

    _**Note**: This will show you all shares created on LON-CL1_

1. Close the command prompt.

1. Right-click **Start**, and then select **Computer Management**.

1. In Computer Management, in the navigation pane, expand **Shared Folders**,
    and then select **Shares**. In the details pane, verify that you see IT and
    Marketing shares, and the default Windows 10 shares.

1. Close Computer Management.

### Task 4: Review configured permissions

1. On LON-CL1, in File Explorer, right-click **IT**, and then select **Properties**.

1. In the IT Properties window, select the **Security tab**, and then select
    **Advanced**.

1. In the Advanced Security Settings for IT dialog box, verify that all the
    permissions entries are set explicitly at this level, because their
    permission inheritance is set to None.

1. Verify that only an Administrator, Administrators (LON-CL1\\Administrators)
    group, SYSTEM and IT (ADATUM\\IT) group have access to the IT folder. These
    settings match the permissions that you configured in the File Sharing
    dialog box.

1. In the Advanced Security Settings for IT dialog box, select **OK**. 

1. In the IT Properties dialog box, select the **Sharing tab**, in the Network File and
    Folder Sharing section, verify that IT now is shared as \\\\lon-cl1\\it, and
    then select **Advanced Sharing**.

1. In the Advanced Sharing dialog box, select **Permissions**. In the
    Permissions for IT dialog box, verify that the Everyone and Administrators
    groups have Full Control permissions to the share, select **OK** twice, and
    then select **Close**.

     _**Note**: If you share a folder by using the File Sharing dialog box, you will
      modify the local file permissions to match your configuration, while the
      Everyone and Administrators groups will have the Full Control share 
      permission._

1. In File Explorer, right-click **Marketing**, and then select **Properties**.

1. In the Marketing Properties window, select the **Security tab**, and then
    select **Advanced**.

1. In the Advanced Security Settings for Marketing dialog box, verify that all
    of the permissions entries are inherited from E:\\. Also verify that Users
    (LON-CL1\\Users) have Read & execute access, while Authenticated Users have
    Modify access, which are the same file permissions as before you shared the
    Marketing folder. Select **OK** twice.

    _**Note**: If you share a folder by using the Advanced Sharing feature, this does
     not modify local file permissions. You only modify share permissions if you
     use Advanced Sharing._

1. Sign out of **LON-CL1**.

### Task 5: Test local file permissions

1. Sign in to **LON-CL1** as **Adatum\\Bill** with the password **Pa55w.rd**.
  
    _**Note**: Bill is a member of the Marketing group, but is not a member of the IT 
    group._

1. Select the **File Explorer** icon on the taskbar.

1. In File Explorer, in the navigation pane, expand **This PC**, expand **AllFiles (E:)**, expand **Data**, and then select **Marketing**.

1. In the details pane, right-click the **empty space**, select **New**, select
    **Text Document**, and then type **File10** as the name of the file.

    _**Note**: Bill has local file permissions to create a new file in the Marketing
    folder, because permissions were configured by using the Advanced Sharing
    feature. This modified only the share permissions, while the default local
    file permissions were not modified. By default, Authenticated Users have the
    Modify permission._

1. In File Explorer, in the navigation pane, select **IT**, and then select
    **Cancel**.

    _**Note**: You will get an error, because Bill does not have local file
    permissions to the IT folder. Permissions were configured by File Sharing,and only members of the IT group have local file permissions to the folder._

1. Sign out of **LON-CL1**.

1. Sign in to **LON-CL1** as **Adatum\\Beth** with the password **Pa55w.rd**.

    _**Note**: Beth is member of the IT group, and she is not member of the Marketing
    group._

1. Select the **File Explorer** icon on the taskbar.

1. In File Explorer, in the navigation pane, expand **This PC**, expand **AllFiles (E:)**, expand **Data**, and then select **Marketing**.

1. In the details pane, verify that you can see File10 that was created by
    Bill.

1. Right-click the **empty space**, select **New**, select **Text Document**, and then type **File20** as the name of the file.

    _**Note**: April has local file permissions to create a new file in the Marketing
    folder because you configured permissions by using the Advanced Sharing
    feature. This modified only the share permissions, while the default local
    file permissions were not modified. By default, Authenticated Users have the
    Modify permission._

1. In File Explorer, in the navigation pane, select **IT**. In the details
    pane, right-click the **empty space**, select **New**, select **Text
    Document**, and then type **File21** as the name of the file.

    _**Note**: April is able to create a file, because you configured permissions by
    using File Sharing. Members of the IT group have local file permissions to
    the IT folder._

    _**Note**: Be aware that Network File and Folder Sharing modifies file
    permissions and share permissions. However, the Advanced Sharing feature
    does not modify file permissions, and only sets share permissions._

1. Sign out of **LON-CL1**.

### Task 6: Test share permissions

1. Switch to **LON-CL2**.

1. Sign in to **LON-CL2** as **Adatum\\Bill** with the password **Pa55w.rd**.

    _**Note**: Bill is a member of the Marketing group, but he is not a member of the IT
    group._

1. Select the **File Explorer** icon on the taskbar.

1. In File Explorer, type **\\\\LON-CL1** in the Address bar, and then press **Enter**.

1. Verify that you can see the IT and Marketing shares in the details pane.

1. Double-click **Marketing**. Verify that you can see the files that Bill and
    Beth created locally.

1. In the details pane, right-click the **empty space**, select **New**, select
    **Text Document**, and then type **File30** as the name of the file. Bill
    has permissions to create a new file in the Marketing share because he is a
    member of the Marketing group.

1. In File Explorer, select **LON-CL1** in the address bar. In the details pane,
    double-click **IT**. Read the text in the Network Error dialog box, and then
    select **Close**.

    _**Note**: Bill is not a member of the IT group, so he does not have permissions
    to the IT share._

1. Sign out of **LON-CL2**.

1. Sign in to **LON-CL2** as **Adatum\\Beth** with the password **Pa55w.rd**.

    _**Note**: Beth is a member of the IT group, but she is not a member of the Marketing
    group._

1. Select the **File Explorer** icon on the taskbar.

1. In File Explorer, type **\\\\LON-CL1** in the Address bar, and then press **Enter**.

1. Verify that you can see the IT and Marketing shares in the details pane.

1. Double-click **Marketing**.

1. Read the text in the Network Error dialog box.

    _**Note**: Beth is not a member of the Marketing group, so she does not have permissions to the Marketing share._

1. Select **Close**.

1. In the details pane, double-click **IT**. Right-click the **empty space** in
    the details pane, select **New**, select **Text Document**, and then type
    **File40** as the name of the file. 

    _**Note**: Beth has permissions to create a new file in the IT share because she is a member of the IT group. Users can connect only to shares that were shared for groups in which	they are members, regardless of whether they were shared by File Sharing or	Advanced Sharing._

1. Sign out of **LON-CL2**.

**Results**: After completing this exercise, you will have created a folder
structure for the Marketing and information technology (IT) departments,
shared their folders, and tested local and share permissions.

## END OF LAB
