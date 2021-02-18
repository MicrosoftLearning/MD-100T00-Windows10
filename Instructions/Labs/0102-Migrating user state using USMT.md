# Practice Lab: Migrating user state using USMT

## Summary

In this lab you will learn how to migrate user state from one computer to another using the User State Migration Tool (USMT).

### Scenario

You have deployed a new Windows 10 computer named Computer1. You need to migrate the user state from a source computer named Win81Source to Computer1. The best way to do so is using the User State Migration Tool (USMT). The USMT install files are located at \\\\SEA-SVR2\\Labfiles\\Install\\USMT. A location to store migration data has been provided at \\\\SEA-SVR2\\Labfiles\\Install\\MigrationStore. For this lab, you will use the IP address 10.10.0.10 to reference SEA-SVR2.

### Task 1: Prepare the source computer

1. Sign in to SEA-SVR2 as **Contoso\\Administrator** with the password **Pa55w.rd**.
2. On SEA-SVR2, on the taskbar, select **Hyper-V Manager**.
3. In Hyper-V Manager, select **SEA-SVR2** and then under **Virtual Machines** select **Win81Source**.
4. From the **Action** menu, select **Connect**, and then select **Start**. After the virtual machine starts, maximize the **Win81Source on SEA-SVR2 - Virtual Machine Connection** window.
5. Sign in to **Win81Source** as **Admin** with the password of **Pa55w.rd**.
6. Right-click the **desktop**, hover over the **New** menu item, and then select **Text Document**. Type **Demofile** and press **Enter**.
7. Double-click **Demofile.txt** and type some random text and then save the file. There should be several items on the desktop including DemoFile.txt and various desktop icons.
8. On the desktop, right-click **This PC** and then select **Manage**.
9. Expand **Local Users and Groups**, and then select **Users**. Notice the local accounts including Admin, LocalUser1 and LocalUser2.
10. Close **Computer Management**.
11. Right-click **Start** and then select **Command Prompt (Admin)** . In the **User Account Control** window select **Yes**.
12. At the command prompt, type the following command, and then press **Enter**:

    ```
    Net Use F: \\10.10.0.10\Labfiles\Install\USMT /user:Contoso\Administrator Pa55w.rd
    ```

13. At the command prompt, type **F:**, and then press **Enter**.

14. At the command prompt, type the following, and then press **Enter**:

    ```
    Scanstate \\10.10.0.10\Labfiles\Install\MigrationStore\Win81 /i:migapp.xml /i:miguser.xml /o
    ```

    _**Note**: This will take several minutes to complete._

15. Close all open windows and then shut down Win81Source.

### Task 2: Complete the migration

1. On SEA-SVR2, on the taskbar, select **Hyper-V Manager**.

2. In Hyper-V Manager, select **SEA-SVR2** and then under **Virtual Machines** select **Computer1**.

3. From the **Action** menu, select **Connect**, and then select **Start**. After the virtual machine starts, maximize the **Computer1 on SEA-SVR2 - Virtual Machine Connection** window.

4. Sign in to **Computer1** as **Admin** with the password of **Pa55w.rd**.

   *Notice that the desktop icons are not visible and there is no Demofile.txt file on the desktop.*

5. Right-click **Start** and then select **Computer Management**.

6. Expand Local Users and Groups, and then select Users.

   *Notice that LocalUser1 and LocalUser2 are not listed.*

7. Select **Start** and type **cmd**. Select **Run as administrator**. In the **User Account Control** window select **Yes**.

8. At the command prompt, type the following command, and then press **Enter**:

    ```
    Net Use F: \\10.10.0.10\Labfiles\Install\USMT /user:Contoso\Administrator Pa55w.rd
    ```

9. At the command prompt, type **F:**, and then press **Enter**.

10. At the command prompt, type the following, and then press **Enter**:

    ```
    Loadstate \\10.10.0.10\Labfiles\Install\MigrationStore\Win81 /i:migapp.xml /i:miguser.xml /lac:Pa55w.rd /lae /c
    ```

11. Type **exit** to close the command prompt.

12. Restore **Computer Management** and refresh the **Users** folder. Notice that LocalUser1 and LocalUser2 are both available.

13. At the Protected Content Migration notice, select **Cancel**.

    *Notice the desktop icons and the DemoFile.txt file migrated from the old computer.*

14. Shut down Computer1.

15. On SEA-SVR2, close Hyper-V Manager.

**END OF LAB**
