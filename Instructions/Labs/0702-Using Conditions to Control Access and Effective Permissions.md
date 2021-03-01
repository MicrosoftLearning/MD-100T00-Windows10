# Practice Lab: Using Conditions to Control Access and Effective Permissions

## Summary
In this lab you will learn how to use conditions to dynamically control access to files based on specific criteria.


### Scenario
Members of the IT, Marketing, and Research departments all require access to file shares located on SEA-CL1, but require different permissions for the data they use. You've been instructed to create a new shared folder in E:\\Data named Research. The Research shared folder should only be accessible by users in the Research Department. The IT shared folder should only by accessible by employees located in the United States who are members of the IT Department. The Active Directory administrator has already configured Dynamic Access Control to allow for you to assign Department and Country based Claim Types to permissions on shared folders.


### Task 1: Configure conditions to control access 
1.  Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**.
    
2.  Select the **File Explorer** icon on the taskbar.

3.  In File Explorer, in the navigation pane, expand **AllFiles (E:)**, and then select **Data**. In the details pane, right-click the empty space, select **New**, select **Folder**, and type **Research** as the new folder name.
    
4.  Right-click **Research**, select **Properties**, select the **Sharing** tab, and then select **Advanced Sharing**.
    
5.  In the Advanced Sharing dialog box, select the **Share this folder** check box, and then select **Permissions**.
    
6.  In the Permissions for Research dialog box, in the Permissions for Everyone section, select the **Change** check box in the Allow column, and then select **OK** twice.
    
7.  In the Research Properties dialog box, select the **Security** tab, select **Advanced**, and then verify that all permissions entries are inherited from E:\\.
    
8.  In the Advanced Security Settings for Research dialog box, select **Users (SEA-CL1\\Users)**, and then select **Remove**. Read the text in the Windows Security dialog box that appears, select **OK**
    
9.  Select **Disable inheritance**.

10. In the Block Inheritance dialog box, select **Convert inherited permissions into explicit permissions on this object**, and then verify that all permissions entries are set explicitly at this level because their
    permission inheritance is set to **None**.
    
11. In the Advanced Security Settings for Research dialog box, select **Users (SEA-CL1\\Users)**, and then select **Remove**. 
    
    _**Note**: The entry for Users is now removed from the Permission entries because it was explicitly set at this level._
    
12. Verify that **Authenticated Users** is selected, and then select **Edit**.

13. In the Permission Entry for Research dialog box, select **Add a condition**, and compose the following expression: **User Department Equals Value Research**. You will need to type research manually in the last box. Select **OK** twice, then select **Close**. 
    
    _**Note**: A claim type for the department attribute was preconfigured for the purpose of this lab._
    
14. In File Explorer, in the navigation pane, select **Data**, right-click **IT**, select **Properties**, select the **Security** tab, and then select **Advanced**.
    
15. In the Advanced Security Settings for IT dialog box, select **IT (Contoso\\it)**, and then select **Edit**.

16. In the Permission Entry for IT dialog box, select **Add a condition**, and compose the following expression: **User Country Equals Value US**. You will need to type US manually in the last field. select **OK** three times.
    
    _**Note**: A claim type for the c (country) attribute was preconfigured for the purpose of this lab._
    
17. Select **OK** twice, then select **Close** to close the IT Properties window.

18. Sign out of SEA-CL1.

### Task 2: Test conditions to control access 

1.  Sign in to **SEA-CL1** as **Contoso\\Briana** with the password **Pa55w.rd**.

3.  Select the **File Explorer** icon on the taskbar.

4.  In File Explorer, type **\\\\SEA-CL1** in the Address bar, and then press **Enter**.

5.  In the details pane, double-click **Research**. Read the text in the Network Error dialog box, and then select **Close**.
    
6.  Select **Start**, type **cmd** and then select **Command Prompt**.

7.  At the command prompt, type the command, `whoami /claims` and then press **Enter**. Review the output, and then **close** the command prompt.
   
    _**Note**: This will show the current claims for the user. Briana has a department claim value of IT and so she cannot connect to the Research share._

8.  In the details pane, double-click **IT**.

9. In the details pane, right-click the empty space, select **New**, select **Text Document**, and then type **File50** as the name of the file.
   
   _**Note**: Briana has permissions to create a new file in the IT share because she is a member of the IT group and her Country claim has a value of US._    

10. Sign out of **SEA-CL1**.

11.  Sign in to **SEA-CL2** as **Contoso\\Mike** with the password **Pa55w.rd**.
     
     _**Note**: Mike is a member of the IT group._

12. Select the **File Explorer** icon on the taskbar.

13. In File Explorer, type **\\\\SEA-CL1** in the Address bar, and then press **Enter**.

14. In the details pane, double-click **IT**. 
    
    _**Note**: Mike is a member of the IT group, but he cannot connect to the IT share._

15. Select **Close**.

16. Select **Start**, type **cmd** and then select **Command Prompt**

17. At the command prompt, type the following command, and then press **Enter** `whoami /claims`. Review the output, and then **close** the command prompt.
    
    _**Note**: Mike has a Country claim with the value of GB, so he cannot connect to the IT share, even though he is a member of the IT group._
    
18. Sign out of **SEA-CL2**.

19. Sign in to **SEA-CL2** as **Contoso\\Davy** with the password **Pa55w.rd**.

20. Select **Start**, type **cmd** and then select **Command Prompt**.

21. At the command prompt, type the following command, `whoami /claims`, and then press **Enter**.

22. Review the output, and then close the command prompt.
   
    _**Note**: Davy is in the Research department, and his department claim has the value of Research._
    
23. Select the **File Explorer** icon on the taskbar.

24. In File Explorer, type **\\\\SEA-CL1** in the Address bar, and then press **Enter**.

25. In the details pane, double-click **Research**, and then verify that Davy can view the contents of the Research folder.
    
26. In the details pane, right-click the **empty space**, select **New**, select **Text Document**, and then type **File60** as the name of the file.
    
    _**Note**: Davy has permissions to create a new file in the Research share because his department claim has a value of Research._
	
27. Sign out of **SEA-CL2**.

### Task 3: View effective permissions 

1.  Switch to **SEA-CL1**.

2. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**.

3. Select the **File Explorer** icon on the taskbar.

4. In File Explorer, browse to **E:\\Data**.

5. In File Explorer, right-click **Marketing**, select **Properties**, select the **Security tab**, select **Advanced**, and then select the **Effective Access** tab.

6. In the Advanced Security Settings for Marketing dialog box, select **Select a user**, in the Enter the object name to select (examples) box, type **Anders**, select **OK**, and then select **View effective access**. View the effective permissions, and then select **OK** twice.

   _**Note**: As Authenticated Users have the Modify permission to the Marketing folder, you can see that Anders has the most permissions allowed._

7. In File Explorer, right-click **Research**, select **Properties**, select the **Security** tab, select **Advanced**, and then select the **Effective Access** tab.

8. In the Advanced Security Settings for Research dialog box, select **Select a user**, in the Enter the object name to select (examples) text box, type **Brian**, select **OK**, in the Multiple Names Found dialog box, review the information and select **OK**, and then select **View effective access**.

   _**Note**: Brian is a member of Development group. Only users with the department claim with a value of Research have permissions to the folder, you can see that Brian has no permissions allowed._

9. In the Advanced Security Settings for Research dialog box, select **Include a user claim**, select **department** in the drop-down list, type **Research** in the Enter value here text box, and then select **View effective access**.

   _**Note**: You can see that if Brian had the department user claim with the value of Research, he would have most permissions allowed._

10. In the Advanced Security Settings for Research dialog box, select **Select a user**, in the Enter the object name to select (examples) box, type **Aaron**, select **OK**, and then select **View effective access**. Review
    the effective permissions, and then select **OK** twice.

    _**Note**: If Aaron had the user claim of department with the value of Research, he would have the most permissions allowed._

11. Sign out of **SEA-CL1**.

**Results**: After completing this exercise, you will have configured and tested conditions to control access to file shares. You will have also viewed effective permissions.

**END OF LAB**
