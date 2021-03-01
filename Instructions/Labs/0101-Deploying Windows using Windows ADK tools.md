# Practice Lab: Deploying Windows using Windows ADK tools 

## Summary

In this lab, you will identify the tools included in the Windows ADK, create bootable Windows PE media, prepare a Windows 10 computer to be imaged, capture a reference Windows 10 image, and deploy a captured Windows 10 image.

### Scenario

As part of the Desktop Administration team at Contoso, you have been tasked with creating and testing a Windows 10 image to be used for a future Windows 10 desktop deployment project. You have already used Hyper-V to create a virtual machine named GoldImage1 and installed Windows 10 to be used as the reference image. You now need to capture GoldImage1 and validate that the image can be deployed to a new computer.

### Task 1: Identify the Windows ADK tools

1.  Sign in to SEA-SVR2 as **Contoso\\Administrator** with the password **Pa55w.rd**.
2.  On the taskbar, select **Start** and then select **Control Panel**.
3.  Select **Programs**, and then select **Programs and Features**. Notice that the **Windows Assessment and Deployment Kit - Windows 10** and the **Windows Assessment and Deployment Kit Windows Preinstallation Environment Add-ons - Windows 10** programs are installed.
4.  Select **Windows Assessment and Deployment Kit - Windows 10** and then select **Change**.
5.  On the **Maintain your Windows Assessment and Deployment Kit - Windows 10 features** page, ensure that **Change** is selected and then select **Next**.
6.  Notice the features that have been installed on SEA-SVR2. Features include:
    - Deployment Tools
    - Imaging and Configuration Designer (ICD)
    - Configuration Designer
    - User State Migration Tool (USMT)
    - Microsoft User Experience Virtualization (UE-V) Template
7.  Select **Cancel** to close the wizard. Select **Yes** and then select **Close**.
8.  Close the **Programs and Features** window.


### Task 2: Create bootable Windows PE media

1.  On SEA-SVR2, select **Start**, expand **Windows Kits**, and then select **Deployment and Imaging Tools Environment**.

2.  At the command prompt type `copype amd64 E:\WinPE`. The Windows PE working files are installed to the target location.

3.  Open **File Explorer** and then browse to **E:\\WinPE**. 

4.  In the **WinPE** folder, select the **media** folder and then select the **sources** folder. Notice the **boot.wim** file located in this folder. This is the boot image that is used for a default configuration of Windows PE. 
5.  Close **File Explorer**.

6. At the command prompt type the following command to create the Windows PE media in ISO format:

```
MakeWinPEMedia /ISO E:\WinPE E:\WinPE\WindowsPE_amd64.iso
```

7. Open **File Explorer** and then browse to **E:\\WinPE**. Notice the **WindowsPE_amd64.iso** file located in this folder. This ISO file will be used to boot an Windows 10 installation to be captured as a gold image.

8. Close **File Explorer**.
### Task 3: Prepare a Windows 10 computer to be imaged

1.  On SEA-SVR2, on the taskbar, select **Hyper-V Manager**.

2.  In Hyper-V Manager, select **SEA-SVR2** and then under **Virtual Machines** select **GoldImage1**.

3. From the **Actions** menu, select **Checkpoint**. A checkpoint is created as shown in the **Checkpoints** pane.

4. From the **Actions** menu, select **Connect**, and in the **GoldImage1 on SEA-SVR2 - Virtual Machine Connection** window, from the **Action** menu, select **Start**. Maximize the **GoldImage1 on SEA-SVR2 - Virtual Machine Connection** window.

5. Sign in to **GoldImage1** as **Admin** with the password of **Pa55w.rd**. 

6. Select the **Start** button, type **command**, and then select **Run as administrator**. At the User Account Control, select **Yes** to open the command prompt with administrative credentials.

7. At the command prompt, ensure that you are at **C:\\Windows\\System32**, and then type the following command and then press Enter:

```
cd sysprep
```

8. At the **C:\\Windows\\System32\\Sysprep** prompt, type the following command and then press Enter:

```
sysprep
```

9. At the **System Preparation Tool 3.1.4** dialog box, ensure that **System Cleanup Action** shows **Enter System Out-of-Box Experience (OOBE)** and then select the check box next to **Generalize**. 

10. Under **Shutdown Options**, select **Shutdown**.

11. Select **OK**. Sysprep generalizes the virtual machine and then shuts down the operating system. This will take a few minutes to complete.

### Task 4: Capture a reference Windows 10 image

1. If necessary, restore the **GoldImage1 on SEA-SVR2 - Virtual Machine Connection** window.

2. From the **GoldImage1 on SEA-SVR2 - Virtual Machine Connection** window, select **Media**, point to **DVD Drive** and then select **Insert Disk**.

3. Browse to **E:\\WinPE**, select **WindowsPE_amd64.iso**, and then select **Open**. You have attached the Windows PE boot disk to the virtual machine.

4. In the GoldImage1 window, from the **Action** menu, select **Start**.
5. As the computer starts, click in the GoldImage1 window and continually press the spacebar to boot from the CD. After the virtual machine starts, maximize the **GoldImage1 on SEA-SVR2 - Virtual Machine Connection** window. Note: If you miss the option to boot from the CD, revert GoldImage1 and redo Task 3.

6. At the command prompt type the following command to configure IP settings for Windows PE:

   `netsh int ipv4 set address "Ethernet" static 10.10.0.11 255.255.255.0`

7. At the command prompt type the following command to map a network location for the image:

   `net use z: \\10.10.0.10\Captures /user:Contoso\Administrator Pa55w.rd`

   The Z drive maps to the Captures shared folder on SEA-SVR2.

8. At the command prompt type the following command to capture the image of the GoldImage1 reference computer:

   `dism /Capture-Image /ImageFile:z:\GoldImage.wim /CaptureDir:d:\ /name:"GoldImage"`

   It will take approximately 15 minutes for the image capture to complete. Continue with the next task while the image capture progresses.

### Task 5: Deploy a captured Windows 10 image 

1.  In Hyper-V Manager, select **SEA-SVR2** and then in the Actions pane, select **New** and then select **Virtual Machine**.

2. On the **Before you Begin** page, select **Next**.

3. On the **Specify Name and Location** page, in the **Name** box type **Computer1**. 

4. Select the check box next to **Store the virtual machine in a different location** and then next to **Location** type **E:\\Labfiles\\VirtualMachines**. Select **Next**.

5. On the **Specify Generation** page, ensure that **Generation 1** is selected and then select **Next**.

6. On the **Assign Memory** page, next to **Startup memory** type **8192** and then select **Next**.

7. On the **Configure Networking** page, next to **Connection**, select **Internal Network** and then select **Next**.

8. On the **Connect Virtual Hard Disk** page, select **Create a virtual hard disk** and enter the following and then click **Next**:

   - Name: Computer1.vhdx
   - Location: E:\\Labfiles\\VirtualMachines
   - Size: 60 GB

9. On the Installation Options page, select **Install an operating system from a bootable CD/DVD-ROM** and configure the following:

   - Image file (.iso): E:\\WinPE\\WindowsPE_amd64.iso

10. Select **Next** and then **Finish**.

11. Restore the GoldImage1 window and verify that the image capture task is complete. When it is complete, close the GoldImage1 window.

12. In Hyper-V Manager, select **SEA-SVR2** and then under **Virtual Machines** select **GoldImage1**.

13. From the **Action** menu, select **Revert** and then in the message box, select **Revert**. GoldImage1 is reverted back to its state prior to performing sysprep.

14. In Hyper-V Manager, select **SEA-SVR2** and then under **Virtual Machines** select **Computer1**.

15. From the **Actions** menu, select **Connect** and then in the **Computer1** window, from the **Action** menu, select **Start**. Maximize the Computer1 window.

16. At the command prompt type the following command to configure IP settings for Windows PE:

    `netsh int ipv4 set address "Ethernet" static 10.10.0.11 255.255.255.0`

17. At the command prompt type the following command to map a network location for the image:

    `net use z: \\10.10.0.10\Captures /user:Contoso\Administrator Pa55w.rd`

    The Z drive maps to the Captures share on SEA-SVR2.

18. At the command prompt type the following commands in order to configure the hard disk on Computer1:

    `Diskpart`

    `List disk`

    `Select disk 0`

    `Clean`

    `Create partition primary size=100`

    `Select partition`

    `Format fs=ntfs quick label=system`

    `Assign letter=f`

    `Active`

    `Create partition primary`

    `Select partition 2`

    `Format fs=ntfs quick label=windows`

    `Assign letter=g`

    `Exit`

19. At the command prompt type the following command to apply the gold image to Computer1:

    `Dism /apply-image /imagefile:Z:\GoldImage.wim /index:1 /ApplyDir:G:\`

20. At the command prompt type the following commands to apply the boot record to the system partition:

    `F:`

    `bcdboot G:\Windows` 

21. Restore the Computer1 window and then from the **Acton** menu, select **Reset**. In the message box, select **Reset**. Computer1 restarts. It will take several minutes for the computer to initialize, and will restart.

22. After Computer1 initializes, complete the following setup tasks:

    - Region: United States
    - Keyboard layout: US
    - Second keyboard: Skip
    - Connect to a network: I don't have internet
    - Connect to the internet: Continue with limited setup
    - License Agreement: Accept

23. On the **Who's going to use this PC**, enter **LocalAdmin** and then select **Next**.

24. On the password and confirm password pages, enter **Pa55w.rd** and then select **Next**.

25. On the security questions page, select and provide answers to three security questions.

26. On the privacy settings page, select **Accept**.

27. On the **Do more across devices with activity history** page, select **Yes**.

28. On the Cortana page, select **Not now**.

29. After the computer signs in, select **Start** and then enter **Control Panel**. Select **Control Panel**.

30. In the Control Panel, select **View network status and tasks**.

31. Select **Change adapter settings** and then select **Ethernet**, select **Properties**, select **Internet Protocol Version 4 (TCP/IPv4)**, enter the following:

    - IP address: 10.10.0.12
    - Subnet mask: 255.255.255.0

32. Select **OK** twice, select **Close**

33. Right-click the **Start** button and then select **System**.

34. In the **About** page, select **Rename this PC**.

35. In the **Rename this PC** dialog box, enter **Computer1** and then select **Next**.

36. Select **Restart later**.

37. Shut down Computer1. 

38. On SEA-SVR2, leave Hyper-V Manager open for the next practice lab.

**Results**: After finishing this lab, you will have successfully prepared and captured a Windows 10 reference computer and deployed a Windows 10 image.

**END OF LAB**
