# Practice Lab: Sideloading an App

## Summary

In this lab you will learn how to sideload a Windows app.

### Scenario

Users in the Research department use a modern app that was developed in-house
called App1.appx. You want to make this app available for all users, so you
decide to sideload the app to test its deployment. Your users require access to
apps available in the Microsoft Store, so you decide to offer a trial of the
installation and update process for apps in the Store. The app and
LeXProductsGrid81_1.1.0.2_AnyCPU certificate have been placed at
\\\\lon-dc1\\labfiles\\apps.

 

### Task 1: Enable Sideloading

1.  Sign in to **LON-CL2** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

2.  On **LON-CL2** select **Start**, and then select the **Settings** icon.

3.  Select **Update & Security**, and then in the navigation pane select **For developers**.

4.  On the **For developers** tab, select **Sideload apps**.

5.  In the **Use developer features** dialog box, select **Yes**.

6.  Close **Settings**.


### Task 2: Install the required certificate

1.  On **LON-CL2**, in the **Type here to search** box, type
    **\\\\lon-dc1\\labfiles\\apps** and press
    **Enter**.

2.  Right-click **LeXProductsGrid81_1.1.0.2_AnyCPU.cer**, and then select
    **Install Certificate**.

3.  On the **Certificate Import Wizard** page, select **Local Machine**, and then
    select **Next**.

4.  On the **User Account Control**, select **Yes**.

5.  On the **Certificate Store** page, sealect **Place all certificates in the
    following store**, select **Browse**, select **Trusted Root Certification
    Authorities**, and then select **OK**.

6.  Select **Next**, and then Select **Finish**.

7.  In the **Certificate Import Wizard** dialog box, confirm that the import was
    successful, and then select **OK**.

8.  Sign out.

 

### Task 3: Install and test an app

1.  Sign in to **LON-CL2** as **Adatum\\Beth** with the password **Pa55w.rd**.

2.  On LON-CL2, in the **Type here to search** box, type
    **\\\\lon-dc1\\labfiles\\apps** and press
    **Enter**.

3.  Double-click **App1.appx**.

4.  In the **Install TestAppTKL1** window, clear the **Launch when ready** check
    box, and then select **Install**.

5.  Close the **TestAppTKL1 is ready!** window.

6.  Select **Start**, scroll down, and then select **TestAppTKL1**.

7.  Close the app.


### Task 4: Remove an app

1.  Select **Start**, right-click **TestAppTKL1** tile, and then select
    **Uninstall**.

2.  In the **This app and its related info will be uninstalled** dialog box,
    select **Uninstall**.

3.  Close all open windows.

4.  Sign out

 

**Results**: During this lab you enabled Sideloading for apps, sideloaded one
app, and uninstalled the sideloaded app.

**END OF LAB**