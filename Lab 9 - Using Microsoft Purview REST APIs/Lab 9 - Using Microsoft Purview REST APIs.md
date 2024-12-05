# Lab 10 – Using Microsoft Purview REST APIs

### **Task 1: Download and Install Postman**

1.  Open a new tab and browse to the **Postman** 
    <https://www.postman.com/downloads/> downloads link on the Lab VM
    browser and click on **Windows 64-bit**.

> ![Screenshot](./media/image1.png)

2.  Click on **Open file** to launch the installer.

> ![Screenshot](./media/image2.png)
>
> ![Screenshot](./media/image3.png)

3.  Once the App is running, click on **Skip and go to the App**.

> ![Screenshot](./media/image4.png)

## Task 2: Register an Application

To invoke the REST API, we must first register an application (i.e.
service principal) that will act as the identity that the Microsoft
Purview platform reognizes and is configured to trust.

1.  Sign in to the **Azure portal**, select the left **Menu** button,
    navigate to **Microsoft Entra ID**

![](./media/image5.png)

2.  On the **Microsoft Entra ID** select **App registrations** and
    click **+ New registration**.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

3.  Provide the application a **name**, select an **account type**, and
    click **Register**.

[TABLE]

![](./media/image7.png)

4.  **Copy** the following values for later use.

    - Application (client) ID

    - Directory (tenant) ID

![A screenshot of a computer Description automatically
generated](./media/image8.png)

## Task 3: Generate a Client Secret

1.  Navigate to **Certifications & secrets** and click **+ New client
    secret**.

![A screenshot of a computer screen Description automatically
generated](./media/image9.png)

2.  Provide the following values and click **Add**.

[TABLE]

![](./media/image10.png)

3.  **Copy** the client secret value for later use.

![](./media/image11.png)

## Task 4: Provide Service Principal Access to Microsoft Purview

1.  Navigate to the **Home** tab of Azure portal and select **All
    resources**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image12.png)

2.  Navigate to the **Microsoft Purview Account** *pvlab-{RandomId}-pv*.

![](./media/image13.png)

3.  Open the **Microsoft Purview Governance Portal**.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

4.  Navigate to the **Data map** \> **Domains** \> **pvlab-{RandomId}-pv
    \> Role assignment**, and then click on the icon of **Add data
    curators**.

![](./media/image15.png)

5.  Search for the name of the Service Principal **purview-spn**, select
    the Service Principal from the search results, and then
    click **OK**.

![](./media/image16.png)

## Task 5: Get an Access Token

1.  Open a new tab on your browser and browse to the **Postman Web App**
    with the given link <https://identity.getpostman.com/login>.

2.  Select **Create account**.

![](./media/image17.png)

3.  Create a new account on **Postman Web App** with your **Office 365
    Admin Tenant** credentials.

4.  Save the **Username** and **Password** for future use.

![](./media/image18.png)

5.  witch back to the **Postman** app launched in Task 1,**Sign-In**
    with your **Username** and **Password**. Complete the
    **Authorization process**.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

6.  Open **Postman Desktop App**, click on **Workspaces** and then
    select **My Workspace**.

![](./media/image20.png)

7.  On your workspace go to **Collections** and create a new **HTTP
    request**.

![](./media/image21.png)

8.  Enter the details below for the new Request.

> ***Note***
>
> *Within the URL, be sure to replace **YOUR_TENANT_ID** with the Tenant
> ID you copied earlier.*

[TABLE]

![](./media/image22.png)

9.  Navigate to **Body**, select **x-wwww-form-urlencoded** and provide
    the following key value pairs.

[TABLE]

10. Once HTTP request is ready, click **Send**.

![](./media/image23.png)

11. If successful, the response will contain an **access token**, copy
    this value for later use.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

## Task 6: Read data from Microsoft Purview

1.  Within the Azure portal, open the **Microsoft Purview account**,
    navigate to **Properties** and find the **Atlas
    endpoint**. **Copy** this value for later use.

![](./media/image25.png)

2.  On the **Postman Desktop App**, create a new **HTTP request**.

![](./media/image26.png)

3.  Enter the following on the **HTTP Request**.

    - **HTTP Method** - GET

    - **URL** - Paste the copied **Atlas endpoint** **value** into the
      **URL** field.
      (e.g. https://YOUR_PURVIEW_ACCOUNT.purview.azure.com/catalog)

    - Add the following at the end of the URL to complete the endpoint:
      /api/atlas/v2/types/typedefs

> *Your URL should be like -
> https://YOUR_PURVIEW_ACCOUNT.purview.azure.com/catalog/api/atlas/v2/types/typedefs*
>
> ***Note***
>
> *Calling this particular endpoint will result in the bulk retrieval of
> all **type definitions**.*

![](./media/image27.png)

> Navigate to **Headers**, provide the following key value pair,
> click **Send**.

[TABLE]

> ***Note***
>
> *You generated an access_token in the previous request. Copy and paste
> this value. Ensure to include the "Bearer " prefix.*

![A screenshot of a computer Description automatically
generated](./media/image28.png)

4.  If successful, Postman should return a **JSON document** in the body
    of the response.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

5.  Click on the **magnifying glass** and search for the following
    phrase **"name": "azure_sql_table"** to jump down to the entity
    definition for an **Azure SQL Table**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

## Task 7 - Clean up Resource

1.  Once all the Labs are completed, we can remove the resource.

2.  Click on the **Portal Menu**, then select **Resource groups**.

> ![Screenshot](./media/image31.png)

3.  Select the **Purviewlab** resource group.

> ![](./media/image32.png)

4.  Click on **Delete resource group**.

> ![](./media/image33.png)

5.  Type the name of the Resource group and then click on
    the **Delete** button.

> ![Screenshot](./media/image34.png)

6.  You should get notification as shown in below image.

> ![Screenshot](./media/image35.png)
