# Practice Lab: Monitoring Events

## Summary

In this exercise you will learn how to monitor events on Windows devices.

### Scenario
You decide to collect event log entries from LON-DC1 on your client LON-CL1. After assigning the required permissions on LON-DC1 you will create a "Collector Initiated" event log subscription that contains the last 30 days of events on LON-CL1. To find critical events and errors really quick you will also create a custom view. 


### Task 1: Configure Event Viewer to collect data from multiple devices
1.  Sign in to **LON-DC1** as **adatum\\Administrator** with the password: **Pa55w.rd**.

2.  Right-click **Start**, and then select **Windows PowerShell (Admin)**.

3.  At the PowerShell command prompt, type the following command, and then press **Enter**:
    ```
    winrm quickconfig
    ```

    _**Note**: This is just a check, as the remote management feature is probably enabled._

4.  In **Server Manager**, select **Tools**, and then select **Active Directory
    Users and Computers**.

5.  In **Active Directory Users and Computers**, in the navigation pane, expand
    **Adatum.com**, and then select **Builtin**.

6.  In the results pane, double-click **Event Log Readers**.

7.  In the **Event Log Readers Properties** dialog box, select the **Members** tab.

8.  Select **Add**, and then in the **Select Users, Contacts, Computers, Service
    Accounts, or Groups** dialog box, select **Object Types**.

9.  In the **Object Types** dialog box, select the **Computers** check box, and
    then select **OK**.

10. In the **Select Users, Contacts, Computers, Service Accounts, or Groups**
    dialog box, in the **Enter the object names to select (examples)** box, type
    **LON-CL1**, and then select **OK**.

11. In the **Event Log Readers Properties** dialog box, select **OK**.

12. Close the **Active Directory users and computers** and Windows PowerShell window

13. Switch to **LON-CL1**.

14. Sign in to **LON-CL1** as **adatum\\Administrator** with the password: **Pa55w.rd**.

15. Right-click **Start**, and then select **Windows PowerShell (Admin)**.

16. At the PowerShell command prompt, type the following command, and then press **Enter**:
    ``` 
    wecutil qc
    ```

17. When prompted, type **Y**, and then press **Enter**.

### Task 2: View and filter events 

1.  On **LON-CL1**, right-click **Start**, and then select **Event Viewer**.

2.  In **Event Viewer**, in the navigation pane, select **Subscriptions**.

3.  Right-click **Subscriptions**, and then select **Create Subscription**.

4.  In the **Subscription Properties** dialog box, in the **Subscription name**
    box, type **LON-DC1 Events**.

5.  Select **Collector Initiated**, and then select **Select Computers**.

6.  In the **Computers** dialog box, select **Add Domain Computers**.

7.  In the **Select Computer** dialog box, in the **Enter the object name to
    select (examples)** box, type **LON-DC1**, and then select **OK**.

8.  In the **Computers** dialog box, select **OK**.

9.  In the **Subscription Properties – LON-DC1 Events** dialog box, select
    **Select Events**.

10. In the **Query Filter** dialog box, select the **Critical**, **Warning**,
    **Information**, **Verbose**, and **Error** Event Level check boxes.

11. In the **Logged** dropdown list, select **Last 30 days**.

12. In the **Event logs** dropdown list, select **Windows Logs**, and then select **OK**.

13. In the **Subscription Properties – LON-DC1 Events** dialog box, select
    **OK**.

14. In **Event Viewer**, in the navigation pane, expand **Windows Logs**.

15. Select **Forwarded Events**.

16. Right-click **Forwarded Events**, and then select **Create Custom View**.

17. In the **Create Custom View** dialog box, select the **Critical** and
    **Error** check boxes, and then select **OK**.

18. In the **Save Filter to Custom View** dialog box, in the **Name** box, type
    **LON-DC1 errors**, and then select **OK**.

19. Examine any listed events. The list may be empty.

20. Close all open windows.

**Results**: After completing this exercise, you will have successfully configured monitoring by using Event Viewer.

**END OF LAB**