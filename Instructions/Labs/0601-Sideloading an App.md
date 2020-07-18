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

1. Sign in to **LON-CL2** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

1. On **LON-CL2** select **Start**, and then select the **Settings** icon.

1. Select **Update & Security**, and then in the navigation pane select **For developers**.

1. On the **For developers** tab, select **Sideload apps**.

1. In the **Use developer features** dialog box, select **Yes**.

1. Close **Settings**.

### Task 2: Install the required certificate

1. On **LON-CL2**, in the **Type here to search** box, type
    **\\\\lon-dc1\\labfiles\\apps** and press
    **Enter**.

1. Right-click **LeXProductsGrid81_1.1.0.2_AnyCPU.cer**, and then select
    **Install Certificate**.

1. On the **Certificate Import Wizard** page, select **Local Machine**, and then
    select **Next**.

1. On the **User Account Control**, select **Yes**.

1. On the **Certificate Store** page, select **Place all certificates in the
    following store**, select **Browse**, select **Trusted Root Certification
    Authorities**, and then select **OK**.

1. Select **Next**, and then Select **Finish**.

1. In the **Certificate Import Wizard** dialog box, confirm that the import was
    successful, and then select **OK**.

1. Sign out.

### Task 3: Install and test an app

1. Sign in to **LON-CL2** as **Adatum\\Beth** with the password **Pa55w.rd**.

1. On LON-CL2, in the **Type here to search** box, type
    **\\\\lon-dc1\\labfiles\\apps** and press
    **Enter**.

1. Double-click **App1.appx**.

1. In the **Install TestAppTKL1** window, clear the **Launch when ready** check
    box, and then select **Install**.

1. Close the **TestAppTKL1 is ready!** window.

1. Select **Start**, scroll down, and then select **TestAppTKL1**.

1. Close the app.

### Task 4: Remove an app

1. Select **Start**, right-click **TestAppTKL1** tile, and then select
    **Uninstall**.

1. In the **This app and its related info will be uninstalled** dialog box,
    select **Uninstall**.

1. Close all open windows.

1. Sign out

**Results**: During this lab you enabled Sideloading for apps, sideloaded one
app, and uninstalled the sideloaded app.

## END OF LAB
