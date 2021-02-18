# Practice Lab: Monitoring Reliability and Performance

## Summary

In this lab, you will learn how to use Task Manager and Reliability Monitor to review Windows 10 reliability and performance. You will also learn how to configure and use Performance Monitor to identify performance issues for a Windows 10 device.

## Exercise 1: Review Windows 10 performance using Task Manager and Reliability Monitor

### Scenario

A user reports performance and speed issues with a client workstation named SEA-CL1. Your first step is to review the Task Manager and Reliability Monitor on SEA-CL1 to identify any noticeable or consistent issues that may be reported  on the computer.

### Task 1: Use Task Manager to review performance

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password: **Pa55w.rd**.
2. Right-click the taskbar and then select **Task Manager**.
3. In the Task Manager window, select **More details**.
4. In the Task Manager window, on the Processes tab, review the running processes.
5. On the taskbar, select **Start**, and then on the Start menu select **Word**.
6. Minimize the **Word** window and then switch to the **Task Manager**. Take note of the **Microsoft Word (32 bit)** process. Also take note of the CPU and Memory used by the application.
7. In the Task Manager, select the **Performance** tab. Take note of the real-time performance of the CPU, Memory and Disk resources.
8. In the Task Manager, select the **App history** tab. Take note of the resource usage and then select **Delete usage history** to reset the counters.
9. In the Task Manager, select the **Startup** tab. Take note of the apps that start up when Windows starts. This will help you identify if any startup apps may be contributing to the performance issues on SEA-CL1.
10. In the Task Manager, select the **Details** tab. Take note of the specific executables running on the machine. This will allow you to identify CPU and Memory usage for specific executables.
11. In the Task Manager, select the **Services** tab. Take note of the services that are running and stopped. You can use this view to Start, Stop, and Restart services as needed.
12. In the Task Manager, select the **Processes** tab.
13. Under Apps, right-click **Microsoft Word (32-bit)** and then select **End task**. This will end the process and force the app to close.
14. Close Task Manager.

### Task 2: Review reliability history using Reliability Monitor

1. On SEA-CL1, on the taskbar, select **Start**, type **reliability**, and then select **View reliability history.** The **Reliability Monitor** opens.
2. In the Reliability Monitor window, select any date that contains an information or warning notification.
3. In the Reliability details section, next to a Warning or Informational event, select **View technical details**.
4. Review the details and then select **OK**.
5. Close the Reliability Monitor.
6. Sign out of SEA-CL1.

**Results**: After completing this exercise, you will have successfully reviewed performance and reliability history using the Task Manager and Reliability Monitor.

## Exercise 2: Monitor Windows 10 using Performance Monitor

### Scenario

You need to use Performance Monitory to identify performance bottlenecks on  the Windows 10 workstation named SEA-CL1. You have developed a script named MonitorScenario.vbs that will simulate and provoke the bad performance on SEA-CL1. While the script runs you plan to monitor the values for  Network Interface Packets per second, PhysicalDisk % Disk Time, PhysicalDisk Avg. Disk Queue Length, Processor % Processor Time and System Processor Queue Length.

### Task 1: Use Performance Monitor to gather a baseline

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password: **Pa55w.rd**.

2. Select **Start**, type **performance**, and then select **Performance Monitor**.

3. In **Performance Monitor**, in the navigation pane, expand **Data Collector Sets**.

4. Select **User Defined**, right-click **User Defined**, point to **New**, and then select **Data Collector Set**.

5. In the **Create new Data Collector Set** wizard, on the **How would you like to create this new data collector set?** page, in the **Name** text box, type **Contoso Baseline**.

6. Select **Create manually (Advanced)**, and then select **Next**.

7. On the **What type of data do you want to include?** page, select the **Performance counter** check box, and then select **Next**.

8. On the **Which performance counters would you like to log?** page, in the **Sample interval** field, type **1**, and then select **Add**.

9. In the **Available counters** list, expand **Network Interface**, select **Packets/sec**, and then select **Add**.

10. In the **Available counters** list, expand **PhysicalDisk**, select **% Disk Time**, and then select **Add**.

11. Under **PhysicalDisk**, select **Avg. Disk Queue Length**, and then select **Add**.

12. In the **Available counters** list, expand **Processor**, select **% Processor Time**, and then select **Add**.

13. In the **Available counters** list, expand **System**, select **Processor Queue Length**, select **Add**, and then select **OK**.

14. On the **Which performance counters would you like to log?** page, select **Next**.

15. On the **Where would you like the data to be saved?** page, select **Next**.

16. On the **Create the data collector set?** page, select **Finish**.

17. In **Performance Monitor**, in the details pane, right-click **Contoso Baseline**, and then select **Start**.

18. Select **Start**, and then select **Word**.

19. Select **Start**, and then select **Excel**.

20. Select **Start**, and then select **PowerPoint**.

21. Close all open Microsoft Office apps, and then switch to **Performance Monitor**.

22. In the navigation pane, right-click **Contoso Baseline**, and then select **Stop**.

23. In **Performance Monitor**, in the navigation pane, expand **Reports**, expand **User Defined**, expand **Contoso Baseline**, and then select the report that has a name beginning with **SEA-CL1**.

24. View the chart. On the menu bar, select the drop-down arrow, and then select **Report**.

25. Record the following values:

    - Network Interface Packets per second

    - PhysicalDisk % Disk Time

    - PhysicalDisk Avg. Disk Queue Length

    - Processor % Processor Time

    - System Processor Queue Length

### Task 2: Simulate load using the load generator script

1. On SEA-CL1, open File Explorer, and browse to **\\\\SEA-DC1\\labfiles\\Support\\**.

2. In the content pane, double-click **CopyMonitor.bat** to copy lab files to the local client.

3. Click Start, type **cmd**. Right-click on **Command Prompt** and select **Run as administrator**.

    _**Note**: The following step initiates a script which generates a resource load. Be sure to continue on to Task 3 **immediately**, before the script completes._

4. In the Command Prompt Window, type each of the following commands and press **Enter**:

    ```powershell
    cd \Monitor
    MonitorScenario.vbs
    ```

### Task 3: Use Performance Monitor to identify possible bottlenecks

1. On SEA-CL1, switch to **Performance Monitor**.

2. Under **Data Collector Sets**, select **User Defined**.

3. Right-click **Contoso Baseline**, and then select **Start**.

4. On the taskbar, in the **Type here to search** type **perfmon /res**, and then press **Enter**.

5. In **Resource Monitor**, which components are under strain?

    _**Note**: Answers will vary depending upon the usage scenario and host configuration, although central processing unit (CPU) and network are likely to be used heavily._

6. After a few minutes, in the **Windows Script Host** prompt, select **OK**.

    _**Note**: Check the taskbar to see if this dialog may be hidden._

7. Wait for the instance of the Command Prompt windows launched by the script to close.

8. Switch to **Performance Monitor**.

9. In the navigation pane, right-click **Contoso Baseline**, and then select **Stop**.

10. In **Performance Monitor**, in the navigation pane, expand **Reports**, expand **User Defined**, expand **Contoso Baseline**, and then select the **second report** that has a name beginning with **SEA-CL1**.

11. View the chart.

12. On the menu bar, select the drop-down arrow, and then select **Report**.

13. Record the component details:

    - Network Interface Packets per second
    - PhysicalDisk % Disk Time
    - PhysicalDisk Avg. Disk Queue Length
    - Processor % Processor Time
    - System Processor Queue Length

14. In your opinion, which components is the script affecting the most?

    _**Note**: The script is affecting the CPU and network, but it is also affecting all counters._

15. Close all open windows and sign out of SEA-CL1.

**Results**: After completing this exercise, you will have successfully use Performance Monitor to determine the cause of a performance bottleneck.

**END OF LAB**