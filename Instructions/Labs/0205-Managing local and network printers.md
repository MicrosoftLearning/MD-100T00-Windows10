# Practice Lab: Managing local and network printers

## Summary

In this exercise, you will perform basic printer configuration. You will add a
local printer by using Devices and Printers. You then will configure printer
security, and use the Print Management tool to add a printer on a remote
computer. You also will connect to a remote printer, and then manage a print
job.

### Scenario

Marketing purchased a new printer that uses a Microsoft PCL6 Class Driver that’s
attached to LON-CL1. They also want to be able to share the printer but restrict
use to just the Managers group. There is a second printer attached to LON-CL2
that uses the Microsoft PS Class Driver, which is also to be shared with access
for everyone to print. After configuring, Beth will need to test that she can
only print to the printer on LON-CL2, and that print jobs initiated from LON-CL2
can be seen in the queue on LON-CL1.

### Task 1: Add and share a local printer

1. Sign in to LON-CL1 as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

1. In the taskbar, in the **Type here to search** text box, type **Control
    Panel**, and then select **Control Panel**.

1. In Control Panel, select **View devices and printers**.

1. In Devices and Printers, select **Add a printer**.

1. In the **Add a device** dialog box, select **The printer that I want isn’t
    listed**.

1. On the **Find a printer by other options** page, select the **Add a local
    printer or network printer with manual settings** option, and then select
    **Next**.

1. On the **Choose a printer port** page, verify that **Use an existing port**
    is selected, and then select **Next**.

1. On the **Install the printer driver** page, in the **Manufacturer** list,
    select **Microsoft**. In the **Printers** list, select **Microsoft PCL6
    Class Driver**, and then select **Next**.

1. On the **Type a printer name** page, in the **Printer name** field, type
    **Managers Printer**, and then select **Next**.

1. On the **Printer Sharing** page, select **Next**, and then select
    **Finish**.

### Task 2: Configure printer security

1. On LON-CL1, in Devices and Printers, right-click **Managers Printer**,
    select **Printer properties**, and then select the **Security** tab.

1. In the **Managers Printer Properties** dialog box, verify that **Everyone**
    is selected, and then select **Remove**.

1. Select **Add**, in the **Enter the object names to select (examples)** box,
    type **Managers**, and then select **OK**. In the **Permissions for
    Managers** section, verify that **Print** check box is selected in the
    **Allow** column, and then select **OK**.

### Task 3: Use Print Management to manage a remote printer

1. On LON-CL1, in the **Type here to search** text box, type **print**, and
    then select **Print Management**.

1. In Print Management, in the navigation pane, expand **Print Servers**, and
    then verify that LON-CL1 is the only print server listed.

1. Right-click **Print Servers**, and then select **Add/Remove Servers**.

1. In the **Add/Remove Servers** dialog box, in the **Add Servers** field, type
    **LON-DC1**, and then select **Add to List**. Type **LON-CL2** in the **Add
    Servers** field, select **Add to List**, and then select **OK**.

1. Verify that the navigation pane lists three print servers.

1. Right-click **LON-CL2**, and then select **Add Printer**.

1. On the **Printer Installation** page, select **Add a new printer using an
    existing port**, and then select **Next**.

1. On the **Printer Driver** page, verify that the **Install a new driver**
    option is selected, and then select **Next**.

1. On the **Printer Installation** page, in the **Manufacturer** list, select
    **Microsoft**. In the **Printers** list, select **Microsoft PS Class
    Driver**, and then select **Next**.

1. On the **Printer Name and Sharing Settings** page, in the **Printer Name**
    box, type **PostScript Printer**, then in the **Share Name** box, type
    **PostScript Printer**, select **Next** twice, and then select **Finish**.

### Task 4: Connect to a remote printer

1. Switch to LON-CL2.

1. Sign in to LON-CL2 as **Adatum\\Beth** with the password **Pa55w.rd**.

    _Note: Beth is member of the IT group, but she is not a member of the
    Managers group._

1. In the taskbar, in the **Type here to search** text box, type **control**,
    and then select **Control Panel**.

1. In Control Panel, select **View devices and printers**.

1. In Devices and Printers, verify that you can see **PostScript Printer**,
    which you added remotely in the previous task.

1. Select **Add a printer**.

1. In the **Add a device** dialog box, select **The printer that I want isn’t
    listed**.

1. On the **Find a printer by other options** page, select **Select a shared
    printer by name**, type **\\\\LON-CL1\\Managers Printer** in the box, and
    then select **Next**.

1. In the **Connect to lon-cl1** dialog box, select **Cancel**. In the box,
    type **\\\\LON-DC1\\Microsoft PS Class
    Driver**, select **Next** twice, and then select **Finish**.

    _Note: Because Beth is not a member of the Managers group, and she does not
    have permissions to \\\\LON-CL1\\Managers Printer, you were asked to type
    credentials that have the appropriate permissions._

1. In Devices and Printers, verify that **Microsoft PS Class Driver on
    LON-DC1** was added.

1. Right-click **Microsoft PS Class Driver on LON-DC1**, and then select **Set
    as default printer**. In the **Printers** dialog box, select **OK**.

1. Verify that the printer has a green check mark next to it, which indicates
    that it is the default printer.

### Task 5: Print a document, and manage a print job

1. On LON-CL2, on the taskbar, in the **Type here to search** text box, type
    **notepad**, and then press Enter.

1. In Notepad, type your name, select the **File** menu, and then select
    **Print**.

1. In the **Print** dialog box, select **Microsoft PS Class Driver on
    LON-DC1**, and then select **Print**.

1. Switch to LON-CL1.

1. On LON-CL1, in Print Management, in the navigation pane, select **Printers
    With Jobs**. In the details pane, view that **Microsoft PS Class Driver** is
    listed and that it has one job in the queue.

1. Switch to LON-CL2

1. On LON-CL2, in the notification area, select **Show hidden icons**,
    right-click the printer icon, and then select **Microsoft PS Class Driver on
    LON-DC1**.

1. In the **Microsoft PS Class Driver on LON-DC1** window, verify that you can
    see a single document called **Untitled – Notepad**. Right-click **Untitled
    – Notepad**, review its properties, and then select **OK**.

1. Right-click **Untitled-Notepad**, select **Cancel**, and then select
    **Yes**.

    _Note: You now have canceled Beth’s print job._

1. Sign out from LON-CL2.

1. Switch to LON-CL1.

1. On LON-CL1, in Print Management, verify that there are no longer any
    printers listed under the **Printers With Jobs** node.

1. Close all open windows

**Results**: After completing this exercises you will have performed basic
printer configuration like adding and sharing a local printer, configuring
printer security, managing and connecting a remote printer and managing a print
job.

## END OF LAB
