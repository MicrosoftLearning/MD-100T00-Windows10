# Practice Lab: Synchronizing files with OneDrive

## Summary

In this lab you will learn how to synchronize content between devices using OneDrive.

### Scenario

Your organization would like to leverage OneDrive as a method for accessing user files from any device. You test this solution by signing in with your Microsoft account and creating a file on SEA-WS2 and verifying that the file automatically synchronizes to SEA-WS1.

*Note: To complete this lab, you need to have a Microsoft account. You can use the Microsoft Account that you configured previously in the Module 3: Synchronizing settings between devices lab. If needed please refer to Module 3 for adding your Microsoft account to SEA-WS1 and SEA-WS2.*

### Task 1: Enable OneDrive sync on SEA-WS2

1.  Sign in to **SEA-WS2** with your Microsoft account and the PIN **1029**.
    
2.  On the task bar, select **File Explorer**, and then select the **OneDrive** node. 
    

_**Note**: The OneDrive node in File Explorer might take several minutes to appear. Please wait for it to appear before proceeding. If it takes longer than 15 minutes, sign out, and then sign back in by using your Microsoft account._

3.  In the File Explorer console tree, expand **OneDrive**, and then select the **Documents** folder. 
    
    *If the Documents folder is not visible, wait approximately 5 minutes for it to appear.* 
    
4. Right-click the empty space in the **Details pane**, select **New**, and then select **Text Document**.

5. Type **File from SEA-WS2** in the **Name** box, and then press Enter.

6. Double-click the document, and when Notepad opens, type **I was here on SEA-WS2**. Press **Ctrl+S**, and then close Notepad.

7. Wait until OneDrive has synchronized the changes indicated by a green check mark symbol in the **Status** row.


_**Note**: If OneDrive indicates it is paused, right-click on the OneDrive status icon, select Resume Syncing._

### Task 2: Sign in to SEA-WS1 with your Microsoft account, and update the synchronized document

1.  Switch to **SEA-WS1**.

2.  Sign in to **SEA-WS1** with your Microsoft account with the PIN **1029**.
    
3.  On the task bar, select **File Explorer**, and then select the **OneDrive** node.
    
4.  In the **File Explorer** console tree, expand **OneDrive**, and then select the **Documents** folder. After a few minutes, the **File from SEA-WS2** document should appear (it can take up to five minutes).
    
    _**Note**: By default OneDrive has the Files On-Demand feature enabled that will download files only on the first use on a device. Such cloud files that have been created Online or on another device are indicated by a cloud symbol in Status._

5.  Double-click the **File from SEA-WS2** document.  
    
    _**Note**: The file will now be downloaded to your device before it will open. If OneDrive indicates it is paused, right-click on the OneDrive status icon, select Resume Syncing._

6.  In the **Notepad** window, directly under the **I was here on SEA-WS2** line, type **Now I’m here on SEA-WS1**, and then press **Enter**.
    
7.  Press **Ctrl+S**, and then close Notepad.

8.  Make a note of the date and time of the **File from SEA-WS2** file.

9.  Switch to **SEA-WS2**.

10.  Check the date and time of the **File from SEA-WS2** document. When it changes to the date and time you noted on **SEA-WS1**, double-click the file (it takes up to five minutes to change). 
        
    _**Note**: You should now see the two lines in Notepad._
    
11. Close Notepad.

12. Right-click the **File from SEA-WS2** document, and select **Always keep on this device.**  

     _**Note**: The check mark symbol in Status will now change to a white check mark in a green circle indicating that this file is always available on your device._

13. Right-click the **File from SEA-WS2** document, and select **Free up space.**  

    _**Note**: This will convert the file back to an online document indicated by the cloud symbol that needs to be downloaded on the first use. This is intended to free up space on your local hard disk._

14. Sign out of **SEA-WS1** and **SEA-WS2**.

**Results**: During this lab you have synchronized files between different devices using OneDrive.

**END OF LAB**