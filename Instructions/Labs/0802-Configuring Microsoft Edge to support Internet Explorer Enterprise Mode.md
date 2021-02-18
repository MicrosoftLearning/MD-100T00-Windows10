# Practice Lab: Configuring Microsoft Edge to support Internet Explorer Enterprise Mode

## Summary

In this lab you will learn how to configure the Internet Explorer Enterprise Mode to provide compatibility for Microsoft Edge to open legacy web sites.

### Scenario

Contoso uses a web site located at intranet.contoso.com. This site currently only works properly using older Internet Explorer versions. As you recently upgraded all devices to Windows 10 and Microsoft Edge Chromium, you must ensure that this web site still opens and works with compatibility mode.

_Dependency Notice: This lab requires that a DNS CNAME entry for intranet.Contoso.com be added which resolves to SEA-SVR1.Contoso.com, as instructed in the Module 5: Configuration and Testing Name Resolution lab. If you did not complete the module 5 lab, complete Exercise 2: Task 2 from that lab before continuing. Also note that Microsoft Edge .admx templates have already been installed to allow for the creation of Microsoft Edge Chromium group policy settings._

### Task 1: Verify the site is not displayed in Enterprise Mode

1. Sign in to **SEA-CL1** as **Contoso\\Cari** with the password **Pa55w.rd**.
2. On the task bar, select **Microsoft Edge**.
3. In the Microsoft Edge window, select **Complete setup**, select **Focused**, and then select **Confirm**.
4. Select **Continue without signing in**.
5. In the Internet Explorer Address bar, type **edge://compat/enterprise**, and then press **Enter**. Notice that the Enterprise Mode Site List does not contain any entries.
6. Sign out of **SEA-CL1**.

### Task 2: Create a Site list for Internet Explorer Enterprise Mode

1. Switch to **SEA-SVR1**.
2. Sign in to **SEA-SVR1** as **Contoso\\Administrator** with the password **Pa55w.rd**.
3. Select the **File Explorer** icon on the taskbar.
4. In File Explorer, browse to **\\\\SEA-DC1\\Labfiles\\Apps**.
5. Double-click the **EMIESiteListManager.msi** file.
6. In the Enterprise Mode Site List Manager Setup window, select **Next**.
7. On the End-User License Agreement page, select the check box for **I accept the terms in the License Agreement**, and then select **Next**.
8. On the Destination Folder page, select **Next**.
9. On the Ready to install Enterprise Mode Site List Manager page, select **Install**.
10. On the Completed the Enterprise Mode Site List Manager Setup Wizard page, select **Finish**.
11. Close File Explorer.
12. Select the **Start** button, type **Enterprise**, right-click **Enterprise Mode Site List Manager** and select **Run as administrator**.
13. In the Enterprise Mode Site List Manager for v.2 schema window, select **Add**.
14. In the Add new website window, in the URL text box, type **intranet.contoso.com**. In the Compat Mode drop-down list box, select **IE9 Document Mode**, and then select **Save**.
15. Select the **File** menu, and then select **Save to XML**.
16. In the Save as… dialog box, navigate to **C:\\inetpub\\wwwroot**. In the File name text box, type **ContosoEnterpriseMode**, and then select **Save**.
17. Close Enterprise Mode Site List Manager.
18. On the task bar, select **Internet Explorer**.
19. In the Internet Explorer window, in the Address bar, type **<http://Intranet.Contoso.com/ContosoEnterpriseMode.xml>**, and then press **Enter**.
20. Verify that the XML file opens correctly.
21. Close Internet Explorer.

### Task 3: Create a policy to enable Internet Explorer Enterprise Mode

1. On SEA-SVR1, switch to **Server Manager**, select **Tools**, and then select **Group Policy Management**.

2. In the Group Policy Management window, expand **Forest: Contoso.com**, expand **Domains**, expand **Contoso.com**, and select **Group Policy Objects**.

3. Right-click **Group Policy Objects**, and then select **New**.

4. In the New GPO dialog box, in the Name box, type **Internet Explorer Enterprise Mode Policy**,
    and then select **OK**.

5. Right-click **Internet Explorer Enterprise Mode Policy**, and then select **Edit**.

6. In the Group Policy Management Editor window, in the left pane, expand **Computer Configuration**, expand **Policies**, expand **Administrative Templates**, and then select **Microsoft Edge**.

7. In the content pane, double-click **Configure Internet Explorer integration**.

8. Select **Enabled**, and then from the **Configure Internet Explorer integration** drop down menu, select **Internet Explorer mode** and then select **OK**.

9. In the content pane, double-click **Configure the Enterprise Mode Site List**.

10. Select **Enabled**, in the **Configure the Enterprise Mode Site List** text box, type **<http://Intranet.Contoso.com/ContosoEnterpriseMode.xml>**, and then select **OK**.

11. Close the Group Policy Management Editor window.

12. In the Group Policy Management window, right-click the **Contoso.com** domain, and then select **Link an existing GPO**.

13. In the Select GPO window, select **Internet Explorer Enterprise Mode Policy**, and select **OK**.

14. Close the Group Policy Management window.

### Task 4: Verify the site is now in enterprise mode

1. Switch to **SEA-CL1** and sign in as **Contoso\\Cari** with the password of **Pa55w.rd**.

2. Select **Start** and type **cmd**. Press **Enter**.

3. At the command prompt, type the following command, and then press Enter.

    `gpupdate /force`

4. On the task bar, select **Microsoft Edge**.

5. In the Internet Explorer Address bar, type **edge://compat/enterprise**, and then press **Enter**. Notice that the Enterprise Mode Site List contains <http://intranet.contoso.com/ContosoEnterpriseMode.xml>.

6. In the Internet Explorer Address bar, type **<http://intranet.Contoso.com>**, and then press **Enter**.

7. Verify that the website displays correctly, and that the Internet Explorer mode icon appears in the address bar. Select the Internet Explorer mode icon to view information about how this site opens.

8. Sign out of **SEA-CL1**.

**Results**: After completing this exercise, you should have successfully configured the Internet Explorer Enterprise Mode for Microsoft Edge.

**END OF LAB**