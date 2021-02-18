# Practice Lab: Monitoring Events

## Summary

In this lab, you will learn how to manage Windows 10 event logs and configure Event log subscriptions.

## Exercise 1: Manage Windows 10 Event Logs

### Scenario

You need to perform maintenance tasks on the Event logs for SEA-CL1. You will first review the event log entries for the Application, Security, and System logs. You will then configure the Maximum log size for the Application and System event logs. Finally, you will configure the Security event log to Archive the log when full and do not overwrite events.

### Task 1: Review Event Log entries

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password: **Pa55w.rd**.
2. Select **Start**, and then type **Event Viewer**.
3. In the search results, select the **Event Viewer** app. The Event Viewer opens.
4. Maximize the Event Viewer window.
5. Under Event Viewer (Local), expand **Windows Logs**.
6. Under Windows Logs, select **Application** and then scroll through the reported events. Take note of the various events listed for the Application log. You may have a combination of Information, Warning, and Error events.
7. Under Windows Logs, select **Security** and then scroll through the reported events. Take note of the events listed for the Security log. Most of these events are security related based upon Microsoft Windows security auditing.
8. Under Windows Logs, select **System** and then scroll through the reported events. Take note of the various events listed for the System log. You may have a combination of Information, Warning, and Error events related to internal Windows system services.
9. With the System log selected, in the Actions pane select **Filter Current Log**.
10. In the Filter Current Log dialog box, on the Filter tab, next to Event level, select the check box next to **Warning** and select the check box next to **Error**.
11. Select **OK** to return to the System log events. Notice that only Warning and Error events are now displayed, since you have filtered out the Information events.
12. In the Actions pane, select **Clear Filter**. All System events are now displayed.
13. In the navigation pane, expand **Applications and Services Logs**. These logs relate to specific services or applications installed on the local machine.
14. Under Applications and Services Logs, expand **Microsoft**, and then expand **Windows**. Notice the variety of log information related to Windows features and services.
15. Under the Windows node, expand **GroupPolicy** and then select the **Operational** log. Take note of the various events listed for the Group Policy Operational log. You may have a combination of Information, Warning, and Error events related to Group Policy processing for the local machine.
16. In the navigation pane, close the **Applications and Services Logs** branch.

### Task 2: Configure Event Log Properties

1. Under Windows Logs, select **Application** and then in the Actions pane, select **Properties**.
2. In the Log Properties - Application dialog box, on the General tab, change the **Maximum log size (KB)** to **2048**.
3. On the General tab, select **Clear log** and then in the Event Viewer prompt select **Clear**.
4. Select **OK** to close the Log Properties - Application dialog box.
5. Under Windows Logs, select **Security** and then in the Actions pane, select **Properties**.
6. In the Log Properties - Security dialog box, on the General tab, change the **Maximum log size (KB)** to **30464**.
7. Under When maximum event log size is reached, select **Archive the log when full, do not overwrite events**.
8. Select **OK** to close the Log Properties - Security dialog box.
9. Close the Event Viewer.

**Results**: After completing this exercise, you will have successfully reviewed event log entries and configured property settings for event logs.

## Exercise 2: Configure and Manage Event Subscriptions

### Scenario

SEA-CL2 is a critical workstation that needs to be monitored and maintained on a regular basis. To efficiently monitor SEA-CL2, you decide to collect its event log entries so that you can review them on your workstation named SEA-CL1. To perform this task, you need to assign permissions on SEA-CL2. You will then create a "Collector Initiated" event log subscription on your workstation that connects to SEA-CL2 and collects the last 30 days of event log entries.

### Task 1: Configure Event Log Subscriptions

1. Sign in to **SEA-CL2** as **Contoso\\Administrator** with the password **Pa55w.rd**.

2. Right-click **Start**, and then select **Windows PowerShell (Admin)**.

3. At the PowerShell command prompt, type the following command, and then press **Enter**:

    ```powershell
    winrm quickconfig
    ```

4. At the PowerShell command type **Y** when prompted. You will be prompted to configure the WinRM service and the WinRM firewall exception.

5. Close Windows PowerShell.

6. Right-click **Start**, and then select **Computer Management**.

7. Expand **System Tools**, expand **Local Users and Groups**, and then select **Groups**.

8. In the results pane, double-click **Event Log Readers**.

9. In the **Event Log Readers Properties** dialog box, select **Add**, and then in the **Select Users, Computers, Service Accounts, or Groups** dialog box, select **Object Types**.

10. In the **Object Types** dialog box, select the **Computers** check box, and then select **OK**.

11. In the **Select Users, Computers, Service Accounts, or Groups** dialog box, in the **Enter the object names to select (examples)** box, type **SEA-CL1**, and then select **OK**.

12. In the **Event Log Readers Properties** dialog box, select **OK**.

13. Close the **Computer Management** window.

14. Switch to **SEA-CL1** and sign in as **Contoso\\Administrator** with the password **Pa55w.rd**.

15. Right-click **Start**, and then select **Windows PowerShell (Admin)**.

16. At the PowerShell command prompt, type the following command, and then press **Enter**:

    ```powershell
    wecutil qc
    ```

17. When prompted, type **Y**, and then press **Enter**.

18. Close the Windows PowerShell window.

### Task 2: View and filter events

1. On **SEA-CL1**, right-click **Start**, and then select **Event Viewer**. Maximize the Event Viewer window.

2. In **Event Viewer**, in the navigation pane, select **Subscriptions**.

3. Right-click **Subscriptions**, and then select **Create Subscription**.

4. In the **Subscription Properties** dialog box, in the **Subscription name** box, type **SEA-CL2 Events**.

5. Select **Collector Initiated**, and then select **Select Computers**.

6. In the **Computers** dialog box, select **Add Domain Computers**.

7. In the **Select Computer** dialog box, in the **Enter the object name to select (examples)** box, type **SEA-CL2**, and then select **OK**.

8. In the **Computers** dialog box, select **OK**.

9. In the **Subscription Properties – SEA-CL2 Events** dialog box, select **Select Events**.

10. In the **Query Filter** dialog box, select the **Critical**, **Warning**, **Information**, **Verbose**, and **Error** Event level check boxes.

11. In the **Logged** dropdown list, select **Last 30 days**.

12. In the **Event logs** dropdown list, select **Windows Logs**, and then select **OK**.

13. In the **Subscription Properties – SEA-CL2 Events** dialog box, select **OK**. A subscription entry named SEA-CL2 events displays with a green circle and white check mark. This indicates that the subscription is active.

14. In **Event Viewer**, in the navigation pane, expand **Windows Logs**.

15. Select **Forwarded Events**.

16. Right-click **Forwarded Events**, and then select **Create Custom View**.

17. In the **Create Custom View** dialog box, select the **Critical** and **Error** check boxes, and then select **OK**.

18. In the **Save Filter to Custom View** dialog box, in the **Name** box, type **SEA-CL2 errors**, and then select **OK**.

19. Examine any listed events. The list may be empty.

20. Close all open windows and then sign out of SEA-CL1.

**Results**: After completing this exercise, you will have successfully configured Event subscriptions by using Event Viewer.

**END OF LAB**