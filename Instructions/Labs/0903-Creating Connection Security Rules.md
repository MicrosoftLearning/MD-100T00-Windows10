# Practice Lab: Creating Connection Security Rules

## Summary
In this exercise you will learn how to create and configure connection security rules to encrypt network traffic between Windows devices.

### Scenario
Your manager wants you to ensure that all network traffic between LON-CL1 and LON-CL2 is encrypted. You configure a connection security rule with the setting "Require authentication for inbound connections and request authentication for outbound connections" enabled on both devices. 

### Task 1: Verify that communications are not secure ###
1.  Sign in to **LON-CL2** as **Adatum\\Administrator** with the password **Pa55w.rd**.

2.  Right-click **Start**, and then select **Windows PowerShell**.

3.  In the Windows PowerShell window, type the following command and then press **Enter**

    ```
    ping LON-CL1
    ```

4.  Verify that the ping generated four “Reply from 172.16.0.162: bytes=32
    Time<*x*ms TTL=128” messages.   

    _**Note**: The times that the message lists may vary from the example._

5.  Select **Start**, type **control** and select **Control Panel**.

6.  Select **System and Security**, and then select **Windows Defender Firewall**.

7.  In the left pane, select **Advanced settings**.

8.  In the left pane, expand **Monitoring,** and then expand **Security
    Associations**.

9.  Select **Main Mode**, and then examine the information in the center pane.   

    _**Note**: No information should be present._

10. Select **Quick Mode**, and then examine the information in the center pane.  

    _**Note**: No information should be present._

11. Switch to **LON-CL1**.

12. Sign in to **LON-CL1** as **Adatum\\Administrator** with the password **Pa55w.rd**.

13. Right-click **Start**, and then select **Windows PowerShell (Admin)**.

14. To examine the Main Mode Security Associations (SAs), at the Windows
    PowerShell prompt, type the following cmdlet, and then press **Enter**:

    ```
    Get-NetIPsecMainModeSA
    ```    

15. To examine the Quick Mode SAs, at the Windows PowerShell prompt, type the
    following cmdlet, and then press **Enter**:

    ```
    Get-NetIPsecQuickModeSA
    ```

     _**Note**: Running each command should produce no result._

### Task 2: Create the Connection Security Rule

1.  On **LON-CL1** select **Start**, type **control** and select **Control Panel** in the list.  

2.  Select **System and Security**, and then Select **Windows Defender Firewall**.  

3.  In the left pane, select **Advanced settings**, and then select **Connection Security Rules**.  

4.  In the Actions pane, select **New Rule**.

5.  On the Rule Type page, verify that **Isolation** is selected, and then select
    **Next**.

6.  On the Requirements page, select **Require authentication for inbound
    connections and request authentication for outbound connections**, and then
    select **Next**.

7.  On the Authentication Method page, select **Computer and user (Kerberos
    V5)**, and then select **Next**.

8.  On the Profile page, select **Next**.

9.  On the Name page, in the Name text box, type **Authenticate all inbound
    connections**, and then select **Finish**.

10. **Close** the Windows Firewall with Advanced Security window.

11. Switch to **LON-CL2**.

12. In the Windows Firewall with Advanced Security window, in the left pane select **Connection Security Rules**.

13. In the Actions pane, select **New Rule**.

14. On the Rule Type page, verify that **Isolation is selected**, and then select **Next**.

15. On the Requirements page, select **Require authentication for inbound
    connections and request authentication for outbound connections**, and then
    select **Next**.

16. On the Authentication Method page, select **Computer and user (Kerberos
    V5)**, and then select **Next**.

17. On the Profile page, select **Next**.

18. On the Name page, in the Name text box, type **Authenticate all inbound
    connections**, and then select **Finish**.

### Task 3: Verify the rule, and monitor the connection ###

1.  In the Windows PowerShell window, type the following command and then press **Enter**
    ```
    ping LON-CL1
    ```

2.  Verify that the ping generated four “Reply from 172.16.0.162: bytes=32 time<*x*ms TTL=128" messages.  

    _**Note**: The information that the message lists may vary from the example._

3.  In the Windows Firewall with Advanced Security window, in the left pane expand **Monitoring,** and then expand **Security Associations**.

4.  Select **Main Mode**, and then examine the information in the center pane.

5.  Select **Quick Mode**, and then examine the information in the center pane.

6.  **Close** all open windows.

7.  Switch to **LON-CL1.**

8.  To examine the Main Mode Security Associations (SAs), at the Windows
    PowerShell command prompt, type the following cmdlet, and then press **Enter**:

    ```
    Get-NetIPsecMainModeSA
    ```

9.  Review the result.

10. To examine the Quick Mode SAs, at the command prompt, type the following
    cmdlet, and then press **Enter**:

    ```
    Get-NetIPsecQuickModeSA
    ```

11. Review the result.

12. Close all open windows

**Results**: After completing this exercise, you should have created and tested connection security rules.

**END OF LAB**