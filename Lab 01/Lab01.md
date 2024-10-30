# Exercise 1: Create an Azure Purview Account

**Prerequisites**

- An Azure Pass subscription. Refer Lab 0 – Setup

- User accounts setup for the implementation. Refer Lab 0 - Setup

- You must have permission to create resources in your Azure
  subscription.

## **Task 1: Register the required resource providers**

Your subscription must have the following resource providers
registered: **Microsoft.Purview**, **Microsoft.Storage**,
and **Microsoft.EventHub**. Follow these steps to complete this
registration.

1.  On the **Home** page of the Azure Portal, Click **Subscriptions**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image1.png)

2.  Now select the **subscription** available in the portal.

![Graphical user interface, text, application, email Description
automatically generated](./media/image2.png)

3.  Browse to **Resource providers** under **Settings** section in the
    left pane as shown in the image.

![Graphical user interface, text, application Description automatically
generated](./media/image3.png)

4.  Now search for **Microsoft.Purview** service and click **Register.**
    This process will take around 2-3 minutes. You can **Refresh** the
    view to see the status.

![Graphical user interface, application, Teams Description automatically
generated](./media/image4.png)

In a similar way, search for and register **Microsoft.Storage**,
**Microsoft.Synapse**, **Microsoft.EventHub** and **Microsoft.Sql**
resources also.

1.  **Microsoft.Storage** resource

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image5.png)

2.  **Microsoft.Synapse** resource

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image6.png)

3.  **Microsoft.EventHub** resource

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image7.png)

4.  **Microsoft.Sql** resource

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image8.png)

## **Task 2: Lab Environment Setup**

1.  Open a new tab on your browser and browse to the given link to open
    the **Custom Deployment page**.
    **!!https://portal.azure.com/#create/Microsoft.Template!!**.

2.  Select **Build your own template in the editor**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

3.  On your lab VM, go to **C:\\labfiles**. Open **azuredeploy.json**
    using **Notepad** and copy the whole contents.

4.  Go to the Azure portal custom deployment page and paste the content
    in the editor. Select **Save**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

5.  Make sure that your **Azure Subscription** is selected automatically
    in the **Subscription** field.

Beneath the **Resource group** field, click **Create new**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

6.   Provide **!!purviewlab-rg!!** as the name of your resource group,
    and then select **OK**.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

7.  Select **East US** for the **Region** field, and then
    click **Review + create**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

8.  Once the validation has passed, click **Create**.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

9.  The deployment should take approximately 10 minutes to complete.
    Once you see the message **Your deployment is complete**, click **Go
    to resource group**.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

10. If successful, you should see a set of 15 resources, like the
    screenshot below.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

Stay on the page and move on to the next part.

## **Task 3: Save your credits**

You can save your credits by stopping the Virtual Machine resource when
you are not using it.

1.  Select the **purviewlab-rg** group. Select the **Virtual Machine**
    resource.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

2.  Click **Stop** and then click **OK**.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

3.  Make sure that the Virtual Machine resource is stopped.

4.  You can click the **Start** tab when you want to use the Virtual
    Machine resource again.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

## **Task 4: Create an Azure Purview Account**

To create and use the Azure Purview platform, you will need to provision
an Azure Purview account.

1.  Sign in to the Azure portal <https://portal.azure.com/>, navigate to
    the **Home** screen, and then click **Create a resource**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

2.  Search the Marketplace for "Azure Purview" and click **Create**.

> ![Graphical user interface, text, application Description
> automatically generated](./media/image21.png)

3.  Provide the inputs given below on the **Basics** tab.

> ***Note**:*
>
> *The Azure resources deployed using the lab template have a randomId.
> It is recommended to use the same randomId for the Microsoft Purview
> account name.*

![A screenshot of a computer Description automatically
generated](./media/image22.png)

[TABLE]

![A screenshot of a computer Description automatically
generated](./media/image23.png)

4.  Select **Review + Create**.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

5.  On the **Review + Create** tab, once the message in the ribbon
    returns "**Validation passed**", verify your selections and
    click **Create**.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

6.  Wait several minutes while your deployment is in progress. Once
    complete, click **Go to resource**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

Stay on the same page and continue to the next exercise.

### **Task 5. Grant Access to Microsoft Purview's Data Plane**

By default, the identity used to create the Microsoft Purview account
resource will have full access to the Microsoft Purview Governance
Portal. The following instructions detail how to provide access to
additional users within your Azure Active Directory.

1.  Navigate to your ***Microsoft Purview account***
    **(pvlab-{*randomId*}-pv)** and click the **Open Microsoft Purview
    Governance Portal** tile.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

2.  Select the checkbox near **This is a public preview. I agree to the
    preview section of the Product Terms C, and Privacy Statements**.
    And select Try now.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

3.  Select **Data map**.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

4.  On the domains page, select **Role assignments** near **Overview**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

5.  Scroll down and on the right-hand side of **Data curators**, click
    the add icon.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

6.  Search for the user **!!Christie Cline!!** within your **Microsoft
    Entra ID** and select the **Account**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

7.  Then select **OK**.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

8.  The **Data Curator** role is now assigned to **Christie Cline** as
    well.

9.  select all the three members added in the **Microsoft Entra ID** and
    click **OK**.

**!\![Johan Adams](urn:gd:lg:a:send-vm-keys)!!**

**!\![Kamala Iyer](urn:gd:lg:a:send-vm-keys)!!**

**!\![Sandy Walker](urn:gd:lg:a:send-vm-keys)!!**

![A screenshot of a computer Description automatically
generated](./media/image34.png)

![A screenshot of a computer Description automatically
generated](./media/image35.png)

![A screenshot of a computer Description automatically
generated](./media/image36.png)

![A screenshot of a computer Description automatically
generated](./media/image37.png)
