# Practice Lab: Joining a Domain

## Summary

In this lab you will join a device to a Windows Active Directory domain.

_Dependency Note: This lab is required to complete in order to complete the_ Monitoring Reliability and Performance lab _later in this course._

### Scenario

You have installed Windows 10 to a new device, LON-CL3. To finalize the setup you will join the device to the adatum.com domain. This will enable the central management of the device and enable other users to log on using their domain credentials.

### Task 1: Verify that no Windows update settings apply via GPO

1. Sign in to **LON-CL3** as **LON-CL3\\Admin** with the password **Pa55w.rd**.

1. Right-click the empty space on the **Desktop**, and then select **Personalize**.

    _**Note**: There is no message indicating that some settings are hidden or managed by your organization__

1. In the **Background** dropdown, check if solid color is available.  

    _**Note**: The dropdown is enabled and a different value can be selected.__

1. Close all open windows.

### Task 2: Join device to domain

1. Select **Start**, and then Select the **Settings** icon.

1. In **Settings**, select **Accounts**.

1. Select **Access work or school**

1. On the Access work or school page, select **Connect**.

1. Select **Join this device to a local Active Directory domain**.

1. On the Join a domain prompt, type **ADATUM** and select **Next**.

1. Type as Username **adatum\\administrator**, type as Password **Pa55w.rd**, and then select **OK**.

1. In the Add account dialog enter **vera** into User account.

1. Select **Restart now**.

### Task 3: Verifiy that device is joined properly

1. Sign in to **LON-CL3** as **ADATUM\\Vera** with the password **Pa55w.rd**

1. Right-click the empty space on the **Desktop**, and then select **Personalize**.

    _**Note**: There is a message indicating that some settings are hidden or managed by your organization. Also the Background dropdown is not enabled._

1. **Sign out**.

1. Login to **LON-CL3** as **Admin** with the password **Pa55w.rd**

    _**Note**: This will fail as domain joined computer always try to login the given user to the domain first. To logon locally that must be explicitly entered._

1. Login to **LON-CL3** as **LON-CL3\\Admin** with the password **Pa55w.rd**

1. In the **Type here to search** box, type **\\\\LON-DC1\\**, and then press Enter.

    _**Note**: As the user is signed in locally to lon-cl3 you are requested to authenticate when trying to access lon-dc1_

1. Select **Cancel**.

**Results**: After completing this exercise you have successfully joined a device to a Windows Active Directory domain.

## END OF LAB
