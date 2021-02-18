# Practice Lab: Managing local and network printers

## Summary

In this exercise, you will perform basic printer configuration. You will add a local printer by using Devices and Printers. You then will configure printer security, and use the Print Management tool to add a printer on a remote computer. You also will connect to a remote printer, and then manage a print job.

### Scenario

The Contoso Marketing department has purchased a new printer that uses a Microsoft PCL6 Class Driver that’s attached to SEA-SVR1. Marketing wants to share the printer but restrict use to just the Managers group. There is another printer attached to SEA-SVR2 that uses the Microsoft PS Class Driver, which is also to be shared with access for everyone to print. You need to configure these printers as requested. After you configure the printers you will have a user named Terry test that she can only print to the printer on SEA-SVR2, and that print jobs initiated from SEA-SVR2 can be seen in the queue on SEA-SVR1.

### Task 1: Add and share a local printer

1. Sign in to SEA-SVR1 as **Contoso\\Administrator** with the password **Pa55w.rd**.

2. Select **Start** and then select **Control Panel**.

3. In Control Panel, select **View devices and printers**.

4. In Devices and Printers, select **Add a printer**.

5. In the **Add a device** dialog box, select **The printer that I want isn’t listed**.

6. On the **Find a printer by other options** page, select the **Add a local printer or network printer with manual settings** option, and then select **Next**.

7. On the **Choose a printer port** page, verify that **Use an existing port** is selected, and then select **Next**.

8. On the **Install the printer driver** page, in the **Manufacturer** list, select **Microsoft**. In the **Printers** list, select **Microsoft PCL6 Class Driver**, and then select **Next**.

9. On the **Type a printer name** page, in the **Printer name** field, type **Managers Printer**, and then select **Next**.

10. On the **Printer Sharing** page, select **Next**, and then select **Finish**.

### Task 2: Configure printer security

1. On SEA-SVR1, in Devices and Printers, right-click **Managers Printer**, select **Printer properties**, and then select the **Security** tab.
2. In the **Managers Printer Properties** dialog box, verify that **Everyone** is selected, and then select **Remove**.
3. Select **Add**, in the **Enter the object names to select (examples)** box, type **Managers**, and then select **OK**. In the **Permissions for Managers** section, verify that **Print** check box is selected in the **Allow** column, and then select **OK**.
4. Close the Devices and Printers window.

### Task 3: Use Print Management to manage a remote printer

1. On SEA-SVR1, select **Start**, type **print**, and then select **Print Management**.
2. In Print Management, in the navigation pane, expand **Print Servers**, and then verify that SEA-SVR1 is the only print server listed.
3. Right-click **Print Servers**, and then select **Add/Remove Servers**.
4. In the **Add/Remove Servers** dialog box, in the **Add Servers** field, type **SEA-SVR2**, and then select **Add to List**.
5. Select **OK**, and then verify that the navigation pane lists two print servers.
6. Right-click **SEA-SVR2**, and then select **Add Printer**.
7. On the **Printer Installation** page, select **Add a new printer using an existing port**, and then select **Next**.
8. On the **Printer Driver** page, verify that the **Install a new driver** option is selected, and then select **Next**.
9. On the **Printer Installation** page, in the **Manufacturer** list, select **Microsoft**. In the **Printers** list, select **Microsoft PS Class Driver**, and then select **Next**.
10. On the **Printer Name and Sharing Settings** page, in the **Printer Name** box, type **PostScript Printer**, then in the **Share Name** box, type **PostScript Printer**, select **Next** twice, and then select **Finish**.
11. Under the **SEA-SVR2** node, select **Printers** and verify that **PostScript Printer** is installed and ready.

### Task 4: Connect to a remote printer

1. Switch to SEA-CL1, and sign in as **Contoso\\Terry** with the password **Pa55w.rd**.

   _Note: Terry is member of the IT group, but she is not a member of the Managers group._

2. In the taskbar, in the **Type here to search** text box, type **control**, and then select **Control Panel**.

3. In Control Panel, select **View devices and printers**.

4. Select **Add a printer**.

5. In the **Add a device** dialog box, select **The printer that I want isn’t listed**.

6. On the **Find a printer by other options** page, select **Select a shared printer by name**, type **\\\\SEA-SVR1\\Managers Printer** in the box, and then select **Next**.

7. In the **Connect to SEA-SVR1** dialog box, select **Cancel**.

8. In the box, type **\\\\SEA-SVR2\\PostScript Printer**, select **Next** twice, and then select **Finish**.

   _Note: Because Terry is not a member of the Managers group, and she does not have permissions to \\\\SEA-SVR1\\Managers Printer, you were asked to type credentials that have the appropriate permissions._

9. In Devices and Printers, verify that **PostScript Printer on SEA-SVR2** was added.

10. Right-click **PostScript Printer on SEA-SVR2**, and then select **Set as default printer**. In the **Printers** dialog box, select **OK**.

11. Verify that the printer has a green check mark next to it, which indicates that it is the default printer.

### Task 5: Print a document, and manage a print job

1. On SEA-CL1, on the taskbar, in the **Type here to search** text box, type **notepad**, and then press Enter.

2. In Notepad, type your name, select the **File** menu, and then select **Print**.

3. In the **Print** dialog box, select **PostScript Printer on SEA-SVR2**, and then select **Print**.

4. Switch to SEA-SVR1.

5. On SEA-SVR1, in Print Management, in the navigation pane, select **Printers With Jobs**. In the details pane, view that **PostScript Printer** is listed and that it has one job in the queue.

6. Switch to SEA-CL1.

7. On SEA-CL1, in the notification area, select **Show hidden icons**, right-click the printer icon, and then select **PostScript Printer on SEA-SVR2**.

8. In the **PostScript Printer on SEA-SVR2** window, verify that you can see a single document called **Untitled – Notepad**. Right-click **Untitled – Notepad**, review its properties, and then select **OK**.

9. Right-click **Untitled-Notepad**, select **Cancel**, and then select **Yes**.

   *Note: You now have canceled Terry's print job.*

10. Sign out from SEA-CL1.
11. Switch to SEA-SVR1.
12. On SEA-SVR1, in Print Management, verify that there are no longer any printers listed under the **Printers With Jobs** node.
13. Close all open windows.
14. Sign out of SEA-SVR1.

**Results**: After completing this exercises you will have performed basic printer configuration like adding and sharing a printer, configuring printer security, managing and connecting a remote printer and managing a print job.

**END OF LAB**