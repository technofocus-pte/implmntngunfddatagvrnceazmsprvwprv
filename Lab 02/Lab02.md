# Lab 2 - Registering & Scanning (ADLS Gen2 and Azure SQL DB)

## Exercise 1: Register & Scan ADLS Gen2 account

In this module, you'll walk through how to register and scan data
sources. You'll create a new collection for your first data source,
upload data and configure scanning. By the end of this module you'll
have technical metadata, such as schema information, stored in Purview.
You can use this to start linking to business terms, allowing your team
members to easier find data.

### Task 1: Grant the Microsoft Purview Managed Identity Access

In this module we will walk through how to grant the Microsoft Purview
system-assigned managed identity the necessary access to successfully
configure and run a scan.

1.  Navigate to the **Home** tab of Azure portal and select **All
    resources**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image1.png)

2.  Select your **Azure Data Lake Storage Gen2 account**
    (e.g. pvlab{randomId}adls).

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image2.png)

3.  Select **Access Control (IAM)** from the left navigation menu.

4.  Click **+ Add** and then click **Add role assignment**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  Filter the list of roles by searching for **Storage Blob Data
    Reader**, click the row to select the role, and then click **Next**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image4.png)

6.  Under **Assign access to**, select **Managed identity**, click **+
    Select members**, select **Microsoft Purview account** from
    the **Managed Identity** drop-down menu, select the managed identity
    for your Microsoft Purview account (e.g. pvlab-{randomId}-pv),
    click **Select**. Finally, click **Review + assign**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image5.png)

7.  Click **Review + assign** once more to perform the role assignment.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image6.png)

8.  Select **Review + assign** again.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image7.png)

9.  To confirm the role has been assigned, navigate to the **Role
    assignments**. You should be able to see that the Microsoft Purview
    managed identity has been granted the **Storage Blob Data
    Reader** role.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image8.png)

10. Select **Access Control (IAM)** from the left navigation menu.

11. Click **+ Add** and then click **Add role assignment**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

12. Filter the list of roles by searching for **Storage Account
    Contributor** , click the row to select the role, and then
    click **Next**.

![](./media/image9.png)

13. Under **Assign access to**, click **+ Select members**,
    select **Microsoft Purview account** from for your Microsoft Purview
    account (e.g. pvlab-{randomId}-pv), click **Select**. Finally,
    click **Review + assign**.

![](./media/image10.png)

14. Click **Review + assign** once more to perform the role assignment.

![](./media/image11.png)

15. You will see a notification – added as Storage Account Contributor
    for pvlab-{randomID}-pv

![A screenshot of a computer Description automatically
generated](./media/image12.png)

### Task 2: Upload Data to Azure Data Lake Storage Gen2 Account

Before proceeding with the following steps, you will need to:

#### Step 1: Download and install Azure Storage Explorer

1.  Open a new tab on your browser and browse to the given link
    <https://azure.microsoft.com/en-us/products/storage/storage-explorer/>.

2.  Select your **Operating system**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

3.  Open the downloaded setup of Azure Storage Explorer. Accept the
    agreement.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image14.png)

4.  To install **.NET 6** select **Next**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image15.png)

5.  Browse the **Destination Location**. Select **Next**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image16.png)

6.  Browse the **Start Menu Folder**. Select **Next**.

![A screenshot of a computer program Description automatically generated
with medium confidence](./media/image17.png)

7.  On completing the setup, select **Finish**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image18.png)

8.  Select **Sign in with Azure**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image19.png)

9.  On the **Select Azure Environment** page, select **Azure** and then
    select **Next**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image20.png)

10. Sign in with your **Office 365 Admi Tenant** credentials.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image21.png)

11. On completing the authentication, return to the **Azure Storage
    Explorer**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image22.png)

12. On **Azure Storage Explorer**, you should verify that your Azure
    account has been added successfully.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image23.png)

#### Step 2: Upload a copy of Bing Coronavirus Query Set on Azure Storage Explorer

1.  Open Azure Storage Explorer, click on the **Toggle Explorer** icon,
    expand the Azure Subscription to find your Azure Storage Account
    (ADLS Gen2). Right-click on Blob Containers and select **Create Blob
    Container**.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

2.  Name the container **raw**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image25.png)

3.  With the container name selected, click on the **Upload** button,
    and select **Upload Folder...**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

4.  Click on the **ellipsis** to select a folder.

![A screenshot of a computer screen Description automatically generated
with low confidence](./media/image27.png)

5.  Navigate and select **BingCoronavirusQuerySet** folder from
    **C:\LabFiles** and click on the **Select Folder** button.

![](./media/image28.png)

6.  Click **Upload**.

![A screenshot of a computer screen Description automatically generated
with low confidence](./media/image29.png)

7.  Monitor the **Activities** until the transfer is complete.

![A picture containing text, line, font, screenshot Description
automatically generated](./media/image30.png)

### Task 3: Create a Collection

1.  Navigate back to the **Home** tab of Azure portal and select **All
    resources**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image1.png)

2.  Open the **Microsoft Purview account** **(pvlab-RandomId-pv)**.

![](./media/image31.png)

3.  Open the **Microsoft Purview Governance Portal**.

![](./media/image32.png)

4.  Navigate to **Data Map** \> **Domains** and click **+ New
    collection**.

![](./media/image33.png)

5.  Enter !!**Contoso!!** in the **Display name** field and
    click **Create**.

![](./media/image34.png)

![](./media/image35.png)

### Task 4: Register a Source (ADLS Gen2)

1.  On the **Microsoft Purview Governance Portal**, navigate to **Data
    Map** \> **Data Sources**, and click on **Register**.

![](./media/image36.png)

2.  Search for Data Lake, select **Azure Data Lake Storage Gen2**, and
    click **Continue**.

![](./media/image37.png)

3.  Select the **Azure subscription**, **Storage account
    name**, **Collection**, and click **Register**.

![](./media/image38.png)

### Task 5: Scan a Source with the Microsoft Purview Managed Identity

1.  On the **Microsoft Purview Governance Portal**, navigate to **Data
    Map** \> **Data Sources**, and within the **Azure Data Lake Storage
    Gen2** tile, click the **New Scan** button.

![](./media/image39.png)

2.  Click **Test connection** to ensure the Microsoft Purview managed
    identity has the appropriate level of access to read the Azure Data
    Lake Storage Gen2 account. If successful, click **Continue**.

![](./media/image40.png)

3.  Expand the hierarchy to see which assets will be within the scans
    scope, and click **Continue**.

![](./media/image41.png)

4.  Select the system default scan rule set and click **Continue**.

![](./media/image42.png)

5.  Select **Once** and click **Continue**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image43.png)

6.  Click **Save and Run**.

![A screenshot of a computer program Description automatically generated
with low confidence](./media/image44.png)

7.  To monitor the progress of the scan run, click **View Details**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image45.png)

8.  Click **Refresh** to periodically update the status of the scan.
    Note: It will take approximately 5 to 10 minutes to complete.

![](./media/image46.png)

![](./media/image47.png)

### Task 6: View Assets

1.  On the **Microsoft Purview Governance Portal** select **Data
    catalog**. On the **Home** tab perform a wildcard search by typing
    the asterisk character (\*) into the search box and hitting the
    Enter key to submit the query.

![A screenshot of a computer Description automatically
generated](./media/image48.png)

2.  You should be able to see a list of assets within the search
    results, which is a result of the scan.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image49.png)

## Exercise 2: Register & Scan Azure SQL DB account

In this exercise, you'll walk through how to register and scan data
sources. You'll create a new collection for your first data source,
upload data and configure scanning. By the end of this exercise you'll
have technical metadata, such as schema information, stored in Purview.
You can use this to start linking to business terms, allowing your team
members to find data more easily.

### Task 1: Key Vault Access Policy \#1 (Grant Yourself Access)

1.  Navigate to the **Home** tab of Azure portal and select **All
    resources**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image1.png)

2.  Select your **Azure Key Vault** resource (Eg. Pvlab
    {RandomId}-keyvault).

![A screenshot of a computer Description automatically
generated](./media/image50.png)

3.  Select **Access policies** and click **+ Create**.

![A screenshot of a computer Description automatically
generated](./media/image51.png)

4.  Under **Secret permissions**, click **Select all**. Then,
    click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image52.png)

5.  Search for your **account name**, select your account name from the
    search results, then click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image53.png)

6.  Skip the **Application (optional)** page by clicking **Next** again.

![A screenshot of a computer Description automatically
generated](./media/image54.png)

7.  Review your selections then click **Create**.

![A screenshot of a computer Description automatically
generated](./media/image55.png)

### Task 2: Key Vault Access Policy \#2 (Grant Microsoft Purview Access)

In this next step, we are creating a second access policy which will
provide Microsoft Purview the necessary access to retrieve secrets from
the Key Vault.

1.  Select **Access policies** again and click **+ Create**.

![A screenshot of a computer Description automatically
generated](./media/image51.png)

2.  Under **Secret permissions**, select **Get** and **List**. Then,
    click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image56.png)

3.  Search for the name of your Microsoft Purview account
    (e.g. pvlab-{randomID}-pv), select the item, then click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image57.png)

4.  Skip the **Application (optional)** page by clicking **Next** again.

![A screenshot of a computer Description automatically
generated](./media/image58.png)

5.  Review your selections then click **Create**.

![A screenshot of a computer Description automatically
generated](./media/image59.png)

![A screenshot of a computer Description automatically
generated](./media/image60.png)

### Task 3: Generate a Secret

In order to securely store our Azure SQL Database password, we need to
generate a secret.

1.  Navigate to **Secrets** and click **Generate/Import**.

![A screenshot of a computer Description automatically
generated](./media/image61.png)

2.  **Copy** and **paste** the values below into the matching fields and
    then click **Create**.

> **Name - sql-secret**
>
> **Value - sqlPassword!**

![A screenshot of a computer Description automatically
generated](./media/image62.png)

![A screenshot of a computer Description automatically
generated](./media/image63.png)

### Task 4: Add Credentials to Microsoft Purview

To make the secret accessible to Microsoft Purview, we must first
establish a connection to Azure Key Vault.

1.  Navigate back to the **Home** tab of Azure portal and select **All
    resources**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image1.png)

2.  Open the **Microsoft Purview account** **(pvlab-RandomId-pv)**.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

3.  Open the **Microsoft Purview Governance Portal**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

4.  Navigate to **Management Center** \> **Credentials**, click **Manage
    Key Vault connections**.

![](./media/image64.png)

5.  Click **New**.

![](./media/image65.png)

6.  **Copy** and **paste** the value below to set the name of your **Key
    Vault connection**, and then use the drop-down menu items to select
    the appropriate **domain**, **Subscription** and **Key Vault name**,
    then click **Create**.

> **Name – KeyVault01**

![](./media/image66.png)

7.  Since we have already granted the Microsoft Purview managed identity
    access to our Azure Key Vault, click **Confirm**.

![A screenshot of a computer error Description automatically
generated](./media/image67.png)

8.  Click **Close**.

![A screenshot of a computer Description automatically
generated](./media/image68.png)

9.  Under **Credentials** click **New**.

![A screenshot of a computer Description automatically
generated](./media/image69.png)

10. Using the drop-down menu items, set the **Authentication
    method** to SQL authentication and the **Key Vault connection** to
    KeyVault01. Once the drop-down menu items are
    set, **Copy** and **paste** the values below into the matching
    fields, and then click **Create**.

- **Name - credential-SQL**

- **User name - sqladmin**

- **Secret name - sql-secret**

![](./media/image70.png)

![A screenshot of a computer Description automatically
generated](./media/image71.png)

### Task 5: Register a Source (Azure SQL DB)

1.  On the **Microsoft Purview Governance Portal**, navigate to **Data
    map** \> **Data Sources**, and click **Register**.

![](./media/image72.png)

2.  Search for SQL Database, select **Azure SQL Database**, and
    click **Continue**.

![](./media/image73.png)

3.  Select the **Azure subscription**, **Server name
    (pvlab-RandomId-sqlsvr)**, and **Collection
    (pvlab-RandomId-pv\>Contoso)**. Click **Register**.

![](./media/image74.png)

### Task 6: Scan a Source with Azure Key Vault Credentials

1.  On the **Microsoft Purview Governance Portal**, navigate to **Data
    map** \> **Sources**, and within the Azure SQL Database tile, click
    the **New Scan** button.

![](./media/image75.png)

2.  Select your **Database** (e.g. pvlab-{randomID}-sqldb), set
    the **Credential** to **credential-SQL**, turn **Lineage
    extraction** to **Off**, and click **Test connection**. Once the
    connection test is successful, click **Continue**.

> ***Note***
>
> *If the "Test connection" appears to be hanging, click Cancel and
> re-try.*

![](./media/image76.png)

3.  Click **Continue**.

![](./media/image77.png)

4.  Click **Continue**.

![A screenshot of a computer Description automatically
generated](./media/image78.png)

5.  Set the trigger to **Once**, click **Continue**.

![](./media/image79.png)

6.  Click **Save and Run**.

![](./media/image80.png)

7.  To monitor the progress of the scan, click **View Details**.

![](./media/image81.png)

8.  Click **Refresh** to periodically update the status of the scan.

> ***Note***
>
> *It will take approximately 5 to 10 minutes to complete.*

![](./media/image82.png)

![A screenshot of a computer Description automatically
generated](./media/image83.png)

### Task 7: View Assets

1.  On the **Microsoft Purview Governance Portal** select **Data
    catalog**. On the **Home** tab perform a wildcard search by typing
    the asterisk character (\*) into the search box and hitting the
    Enter key to submit the query.

![A screenshot of a computer Description automatically
generated](./media/image48.png)

2.  You should be able to see a list of assets within the search
    results, which is a result of the scan.

![A screenshot of a computer Description automatically
generated](./media/image84.png)
