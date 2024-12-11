# Lab 0: Setting up your Lab Environment

## Task 1: Creating the user accounts

1.  Open your browser, navigate to the address bar, and type or paste
    the following URL: **!!https://portal.azure.com/!!**, then press the
    **Enter** button.

2.  In the **Microsoft Azure** window, use the **User Credentials** to
    login to Azure.

    ![](./media/image2.png)

3.  Then, enter the password and click on the **Sign in** button**.**

      ![](./media/image9.png)

4.  In **Stay signed in?** window, click on the **Yes** button.

     ![](./media/image10.png)
     ![](./media/image11.png)

5.  On the Azure Portal and search for **Microsoft Entra ID.** Select
    the option from the list displayed accordingly.

     ![](./media/image12.png)

6.  On the left navigation pane, select the **Users** tab
    under **Manage** section.

      ![](./media/image13.png)

7.  To create a user drop down the **Add** and select **User** and click
    on the **Create new user.**

8.  Enter the **User Principal** Name as !!**chris**!!, enter the
    Display Name as !!**Chris Green**!!, and click on **'Next:
    Properties.**

      ![](./media/image14.png)

5.  Click on the **Next: Assignments.**

      ![](./media/image15.png)

6.  In the **Assignments** tab, select organizer and click on the
    **Review+submit**

      ![](./media/image16.png)
     
      ![](./media/image17.png)
     
      ![](./media/image18.png)

7.  In the **Review+submit** tab, once the Validation is Passed, click
    on the **Create** button.

      ![](./media/image18.png)

9.  You should see all the uploaded users under **All users** tab as
    shown in below image.

     ![](./media/image19.png)

## Task 2: Register the required resource providers

Your subscription must have the following resource providers registered:
**Microsoft.Purview**, **Microsoft.Storage**, **Microsoft.Synapse**,
**Microsoft.EventHub** and **Microsoft.Sql**. Follow the steps given
below to complete the registration.

1.  On the **Home** page of the Azure Portal, Click **Subscriptions**.

    ![](./media/image7.png)

2.  Select the Azure subscription which you have activated in Task 1.

     ![](./media/image8.png)

3.  Select **Resource providers** under the **Settings** section in the
    left pane.

     ![](./media/image20.png)

4.  Search for **Microsoft.Purview** service and click **Register.** It
    will take around 2-3 minutes to complete the registration. You can
    **Refresh** the view to see the status.

    ![](./media/image21.png)
    ![](./media/image22.png)

5.  In a similar way, search for and register **Microsoft.Storage**,
    **Microsoft.Synapse**, **Microsoft.EventHub,** **Microsoft.Sql,**
    **Microsoft.DataFactory,** **Microsoft.Insights** and
    **Microsoft.KeyVault** resources also.

    a.  **!!Microsoft.Storage!!** resource
        ![](./media/image23.png)

    b.  **!!Microsoft.Synapse!!** resource
        ![](./media/image24.png)

    c.  **!!Microsoft.EventHub!!** resource
        ![](./media/image25.png)

    d.  **!!Microsoft.Sql!!** resource

       ![](./media/image26.png)

    e.  **!!Microsoft.DataFactory!!** resource

        ![](./media/image27.png)

    f.  **!!Microsoft.Insights!!** resource

       ![](./media/image28.png)

    g.  **!!Microsoft.KeyVault!!** resource

       ![](./media/image29.png)

## Task 3: Lab Environment Setup

1.  Open a new tab on your browser and browse to the given link to open
    the **Custom Deployment page**.     !!https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ftayganr%2Fpurviewlab%2Fmain%2Ftemplate%2Fazuredeploy.json!!

2.  Select **Build your own template in the editor**.

    ![](./media/image30.png)

3.  On your lab VM, go to **C:\\labfiles**. Open **azuredeploy.json**
    using **Notepad** and copy the whole contents.

4.  Go to the Azure portal custom deployment page and paste the content
    in the editor. Select **Save**.

     ![](./media/image31.png)

5.  Make sure that your **Azure Subscription** is selected automatically
    in the **Subscription** field.

6.  In the **Resource group** field, click **Create new.** Provide
    **!!purviewlab-rg!!** as the name of your resource group, and then
    select **OK**.

    ![](./media/image32.png)
    
     ![](./media/image33.png)

    Note: Select available a region, in this lab **West US** is using for
    this resource.

    ![](./media/image34.png)

     ![](./media/image35.png)
    
    ![](./media/image36.png)

7.  Select **West US** for the **Region** field, and then
    click **Review + create**.

     ![](./media/image37.png)

8.  Once the validation has passed, click **Create**.

     ![](./media/image38.png)

9.  The deployment should take approximately 10 minutes to complete.
    Once you see the message **Your deployment is complete**, click **Go
    to resource group**.

     ![](./media/image39.png)

10. If successful, you should see a set of 15 resources, like the
    screenshot below.

      ![](./media/image40.png)

Stay on the page and move on to the next part.

## Task 4: Save your credits

You can save your credits by stopping the Virtual Machine resource when
you are not using it.

1.  Select the **purviewlab-rg** group. Select the **Virtual Machine**
    resource.

    ![](./media/image41.png)

2.  Click **Stop** and then click **OK**.

     ![](./media/image42.png)

     ![](./media/image43.png)

    ![](./media/image44.png)

3.  Make sure that the Virtual Machine resource is stopped.

4.  You can click the **Start** tab when you want to use the Virtual
    Machine resource again.

    ![](./media/image45.png)
