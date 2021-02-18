# Practice Lab: Using Advanced Startup and Windows RE to recover from Boot Failures

## Summary

During this lab you will learn how to work with the Windows RE, manipulate the BCD from the Command Prompt tool, and use Startup Settings to access advanced startup options.

### Scenario

You need to test and validate the features available for when you need to recover from boot failures on a Windows 10 device. You will access Windows RE to identify the recovery options that are available. You will also use command-line tools to manipulate the BCD and use Startup Settings to access the advanced startup options.

### Lab Preparation

To complete this lab you need to attach **Win10_20H2_Eval.iso** to SEA-CL2. Consult with your instructor on how to perform this task.

### Task 1: Use Windows RE

1. Restart SEA-CL2.
2. When prompted to **Press any key to boot from CD or DVD**, select the spacebar. The computer starts into Windows Setup.
3. In Windows Setup, select **Next**.
4. On the **Install now** page, select **Repair your computer**.
5. On the **Choose an option** page, select **Troubleshoot**.
6. On the **Advanced options** page, notice the five tools that are available.
7. Select **Command Prompt**.
8. At the command prompt, enter **diskpart**, and then select Enter.
9. At the command prompt, enter **list disk**, and then select Enter.
10. At the command prompt, enter **list volume**, and then select Enter.
11. At the command prompt, enter **exit**, and then select Enter.
12. At the command prompt, enter **d:**, and then select Enter.
13. At the command prompt, enter **dir**, and then select Enter. This is the system drive.
14. At the command prompt, enter **cd\\windows\\system32**, and then select Enter.
15. At the command prompt, enter **net start**, and then select Enter. A list of running services is returned.
16. At the command prompt, enter **sc query**, and then select Enter. A list of services and their current status is returned.
17. At the command prompt, enter **regedit**, and then select Enter. The Registry Editor opens.
18. Close the Registry Editor.
19. At the command prompt, enter **exit**, and then select Enter.
20. On the Choose an option page, select **Troubleshoot**.
21. On the Advanced options page, select **Startup Repair**.
22. On the Startup Repair page, select **Windows 10**. Automatic startup repair begins.
23. On the Startup Repair page, notice the log file (D:\\Windows\\System32\\Logfiles\\Srt\\SrtTrail.txt) mentioned in the message.
24. Select **Advanced options**.
25. On the Choose an option page, select **Continue**.
26. Sign in as **Contoso\\Administrator** by using the password **Pa55w.rd**.
27. On the taskbar, select the **File Explorer** icon.
28. In File Explorer, navigate to **C:\\Windows\\System32\\Logfiles\\Srt**.
29. In the Srt folder, open **SrtTrail.txt**.
30. Examine the file for any errors. There should be none.
31. Close the file, and then close File Explorer.

### Task 2: Work with BCD

1. On SEA-CL2, select **Start**, and then select **Settings**.
2. In Settings, select **Update & Security**.
3. Select **Recovery**.
4. In the results pane, under **Advanced startup**, select **Restart now**.
5. On the Choose an option page, select **Troubleshoot**.
6. On the Troubleshoot page, select **Advanced options**.
7. On the Advanced options page, select **Command Prompt**. SEA-CL2 restarts into the Command Prompt mode.
8. On the Command Prompt page, select **Admin**. This is the local administrator account.
9. In the Password box, enter **Pa55w.rd**, and then select **Continue**.
10. At the command prompt, enter **bcdedit /enum**, and then select Enter. This lists the available boot options in the store.
11. At the command prompt, enter **bootrec /scanos**, and then select Enter. This command scans the partitions for viable operating systems.
12. At the command prompt, enter **bootrec /rebuildbcd**, and then select Enter. This command rebuilds the boot store automatically.
13. At the command prompt, enter **exit**, and then select Enter.
14. On the Choose an option page, select **Continue**.
15. Sign in as **Contoso\\Administrator** by using the password **Pa55w.rd**.

### Task 3: Access Advanced Startup options

1. On SEA-CL2, in the **Type here to search** box, enter **msconfig.exe**, and then select Enter. The System Configuration application opens.
2. In the System Configuration dialog box, select the **Boot** tab.
3. On the Boot tab, select the **Safe boot** check box, and then select **OK**.
4. In the System Configuration dialog box, select **Restart**.
5. When the computer restarts, sign in as **Contoso\\Administrator** by using the password **Pa55w.rd**. Notice that the desktop now displays Safe Mode in each corner.
6. Right-click **Start** or activate its context menu, and then select **Run**.
7. In the Run box, enter **msconfig.exe**, and then select Enter.
8. In the System Configuration dialog box, on the General tab, select **Normal startup**, and then select **OK**.
9. In the System Configuration dialog box, select **Restart**.
10. When the computer restarts, sign in as **Contoso\\Administrator** by using the password **Pa55w.rd**. Notice that the Windows operating system starts normally.
11. On SEA-CL2, select **Start**, and then select **Settings**.
12. In Settings, select **Update & Security**.
13. Select **Recovery**.
14. In the results pane, under Advanced startup, select **Restart now**.
15. On the Choose an option page, select **Troubleshoot**.
16. On the Troubleshoot page, select **Advanced options**.
17. On the Advanced options page, select **Startup Settings**.
18. On the Startup Settings page, select **Restart**.
19. When the computer restarts, on the Startup Settings page, select Enter to start normally.

**Results**: After completing this exercise, you should have started Windows RE, manipulated the BCD from the Command Prompt tool, and used Startup Settings to access advanced startup options.

**END OF LAB**