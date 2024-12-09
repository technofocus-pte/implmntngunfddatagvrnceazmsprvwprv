# Lab 2 - Registering & Scanning (ADLS Gen2 and Azure SQL DB)

**Introduction**

To populate Microsoft Purview with assets for data discovery and
understanding, you must register sources that exist across our data
estate so that we can leverage the out of the box scanning capabilities.
Scanning enables Microsoft Purview to extract technical metadata such as
the fully qualified name, schema, data types, and apply classifications
by parsing a sample of the underlying data.

In this lab, you'll walk through how to register and scan data sources.
You'll create a new collection for your first data source, upload data
and configure scanning. By the end of this module you'll have technical
metadata, such as schema information, stored in Purview. You can use
this to start linking to business terms, allowing your team members to
easier find data.

**Objectives**

- Create a collection.

- Register and scan an Azure Data Lake Storage Gen2 account using the
  Microsoft Purview managed identity.

## Exercise 1: Register & Scan ADLS Gen2 account

### Task 1: Grant the Microsoft Purview Managed Identity Access

In this module we will walk through how to grant the Microsoft Purview
system-assigned managed identity the necessary access to successfully
configure and run a scan.

1.  Navigate to the **Home** tab of Azure portal and select **All
    resources**.

     ![](./media/image1.png)

2.  Select your **Azure Data Lake Storage Gen2 account**
    (e.g. pvlab{randomId}adls).

     ![](./media/image2.png))

3.  Select **Access Control (IAM)** from the left navigation menu.

4.  Click **+ Add** and then click **Add role assignment**.

     ![](./media/image3.png)

5.  Filter the list of roles by searching for !!**Storage Blob Data Reader!!**, click the row to select the role, and then
    click **Next**.

      ![](./media/image4.png)

6.  Under **Assign access to**, select **Managed identity**, click **+Select members**, select **Microsoft Purview account** from the **Managed Identity** drop-down menu, select the managed identity for your Microsoft Purview account (e.g. pvlab-{randomId}-pv),click **Select**. Finally, click **Review + assign**.

     ![](./media/image5.png)
7.  Click **Review + assign** once more to perform the role assignment.

    ![](./media/image6.png)

8.  Select **Review + assign** again.

     ![](./media/image7.png)

9.  To confirm the role has been assigned, navigate to the **Role
    assignments**. You should be able to see that the Microsoft Purview
    managed identity has been granted the **Storage Blob Data
    Reader** role.

      ![](./media/image8.png)

10. Select **Access Control (IAM)** from the left navigation menu.

11. Click **+ Add** and then click **Add role assignment**.

    ![](./media/image9.png)

12. Filter the list of roles by searching for **Storage Account
    Contributor** , click the row to select the role, and then
    click **Next**.

    ![](./media/image10.png)

13. Under **Assign access to**, click **+ Select members**,
    select **Microsoft Purview account** from for your Microsoft Purview
    account (e.g. pvlab-{randomId}-pv), click **Select**. Finally,
    click **Review + assign**.

      ![](./media/image11.png)

14. Click **Review + assign** once more to perform the role assignment.

      ![](./media/image12.png)

15. You will see a notification – added as Storage Account Contributor
    for pvlab-{randomID}-pv

     ![](./media/image13.png)

### Task 2: Upload Data to Azure Data Lake Storage Gen2 Account

1.  In the Azure Data Lake in the Overview page. In the left-side
    navigation pane, navigate to **Data storage** section, then click on
    **Containers**. Click on **+Container**

      ![](./media/image14.png)

2.  On the New container pane that appear on the right side, enter the
    container **Name** as **!!raw!!** and click on **Create** button.

      ![](./media/image15.png)

3.  On **Azure storage | Containers** page, select **raw**
    container.

      ![](./media/image16.png)

4.  On **raw** container page, click on **Upload** button.

      ![](./media/image17.png)

5.  In the **Upload blob** pane, click on **Browse for file**, navigate
    to **C:\Labfiles** location and select **2020 folder**, then click
    on the **Open** button.

     ![](./media/image18.png)

      ![](./media/image19.png)

6.  In the **Upload blob** pane, drop down the Advanced, enter **2020**
    as **Upload to folder** and click on **Upload**

      ![](./media/image20.png)

     ![](./media/image21.png)

7.  On **raw** container page, click on **Upload** button.

     ![](./media/image22.png)

8.  In the **Upload blob** pane, click on **Browse for file**, navigate
    to **C:\Labfiles** location and select **2021 folder**, then click
    on the **Open** button.

      ![](./media/image23.png)

9.  In the **Upload blob** pane, drop down the Advanced, enter **2021**
    as **Upload to folder** and click on **Upload**

      ![](./media/image24.png)

      ![](./media/image25.png)

### Task 3: Create a Collection

1.  Navigate back to **Microsoft Purview resource group**
    **(purviewlab-rg)**.

      ![](./media/image26.png)

2.  Open the **Microsoft Purview account** **(pvlab-RandomId-pv)**.

      ![](./media/image27.png)

3.  Open the **Microsoft Purview Governance Portal**.

      ![](./media/image28.png)

4.  Navigate to **Data Map** \> **Domains** and click **+ New
    collection**.

    ![](./media/image29.png)
    
    ![](./media/image30.png)

5.  Enter **!!Contoso!!** in the **Display name** field and
    click **Create**.

    ![](./media/image31.png)

    ![](./media/image32.png)

### Task 4: Register a Source (ADLS Gen2)

1.  On the **Microsoft Purview Portal**, navigate to **Data
    Map** \> **Data Sources**, and click on **Register**.

      ![](./media/image33.png)

2.  Search for !!**Data Lake!!**, select **Azure Data Lake Storage
    Gen2**, and click **Continue**.

     ![](./media/image34.png)

3.  Select the **Azure subscription**, **Storage account
    name**, **Collection**, and click **Register**.

      ![](./media/image35.png)
      ![](./media/image36.png)

### Task 5: Scan a Source with the Microsoft Purview Managed Identity

1.  On the **Microsoft Purview Portal**, navigate to **Data
    Map** \> **Data Sources**, and within the **Azure Data Lake Storage
    Gen2** tile, click the **New Scan** button.

      ![](./media/image37.png)

2.  Click **Test connection** to ensure the Microsoft Purview managed
    identity has the appropriate level of access to read the Azure Data
    Lake Storage Gen2 account. If successful, click **Continue**.

      ![](./media/image38.png)

3.  Expand the hierarchy to see which assets will be within the scans
    scope, and click **Continue**.

      ![](./media/image39.png)

4.  Select the system default scan rule set and click **Continue**.

      ![](./media/image40.png)

5.  Select **Once** and click **Continue**.

      ![](./media/image41.png)

6.  Click **Save and Run**.

     ![](./media/image42.png)

7.  To monitor the progress of the scan run, click **View Details**.

      ![](./media/image43.png)

8.  Click **Refresh** to periodically update the status of the scan.
    Note: It will take approximately 5 to 10 minutes to complete.

      ![](./media/image44.png)
   
     ![](./media/image45.png)

### Task 6: View Assets

1.  On the **Microsoft Purview Governance Portal**, navigate
    to **Unified Catalog** , expand  **Discovery** and select **Data
    assets**, type the asterisk character (**\***) into the search bar,
    and hit **Enter**.

      ![](./media/image46.png)

2.  You should be able to see a list of assets within the search
    results, which is a result of the scan.

     ![](./media/image47.png)

## Exercise 2: Register & Scan Azure SQL DB account

To populate Microsoft Purview with assets for data discovery and
understanding, we must register sources that exist across our data
estate so that we can leverage the out of the box scanning capabilities.
Scanning enables Microsoft Purview to extract technical metadata such as
the fully qualified name, schema, data types, and apply classifications
by parsing a sample of the underlying data.

In this exercise, you'll walk through how to register and scan data
sources. You'll create a new collection for your first data source,
upload data and configure scanning. By the end of this exercise you'll
have technical metadata, such as schema information, stored in Purview.
You can use this to start linking to business terms, allowing your team
members to find data more easily.

### Task 1: Key Vault Access Policy \#1 (Grant Yourself Access)

1.  Navigate to the **Home** tab of Azure portal and select **All
    resources**.

      ![](./media/image48.png)

2.  Select your **Azure Key Vault** resource (Eg. Pvlab
    {RandomId}-keyvault).

     ![](./media/image49.png)

3.  In the **Key vault** home page, select **Access policies** and
    click **+ Create**.

      ![](./media/image50.png)

4.  Under **Secret permissions**, click **Select all**. Then,
    click **Next**.

     ![](./media/image51.png)

5.  Search for your **account name**, select your account name from the
    search results, then click **Next**.

      ![](./media/image52.png)

6.  Skip the **Application (optional)** page by clicking **Next** again.

      ![](./media/image53.png)

7.  Review your selections then click **Create**.

      ![](./media/image54.png)

      ![](./media/image55.png)
### Task 2: Key Vault Access Policy \#2 (Grant Microsoft Purview Access)

In this next step, we are creating a second access policy which will
provide Microsoft Purview the necessary access to retrieve secrets from
the Key Vault.

1.  In the **Key vault** home page, select **Access policies** and
    click **+ Create**.

      ![](./media/image56.png)

2.  Under **Secret permissions**, select **Get** and **List**. Then,
    click **Next**.

      ![](./media/image57.png)

3.  Search for the name of your **Microsoft Purview account**
    (e.g. pvlab-{randomID}-pv), select the item, then click **Next**

      ![](./media/image58.png)

4.  Skip the **Application (optional)** page by clicking **Next** again.

      ![](./media/image59.png)

5.  Review your selections then click **Create**.

     ![](./media/image60.png)

      ![](./media/image61.png)

### Task 3: Generate a Secret

In order to securely store our Azure SQL Database password, we need to
generate a secret.

1.  Navigate to **Secrets** and click **Generate/Import**.

      ![](./media/image62.png)

2.  **Copy** and **paste** the values below into the matching fields and
    then click **Create**.

    **Name - !!sql-secret!!**
   
    **Value - !!sqlPassword!!!**
 
    ![](./media/image63.png)

    ![](./media/image64.png)

### Task 4: Add Credentials to Microsoft Purview

To make the secret accessible to Microsoft Purview, we must first
establish a connection to Azure Key Vault.

1.  Navigate back to the **Home** tab of Azure portal and select **All
    resources**.

      ![](./media/image1.png)

2.  Open the **Microsoft Purview account** **(pvlab-RandomId-pv)**.

      ![](./media/image65.png)

3.  Open the **Microsoft Purview Governance Portal**.

      ![](./media/image66.png)

4.  Navigate to **Data Map**, dropdown the **Source management** and
    click on **Credentials.**
    ![](./media/image67.png)

5.  In the Credentials pane, click **Manage Key Vault connections**.

     ![](./media/image68.png)

6.  In the **Manage Key Vault connections** tab, Click **New**.

     ![](./media/image69.png)

7.  **Copy** and **paste** the value below to set the name of your **Key
    Vault connection**, and then use the drop-down menu items to select
    the appropriate **domain**, **Subscription** and **Key Vault name**,
    then click **Create**.

      **Name – !!KeyVault01!!**

      ![](./media/image70.png)

8.  Since we have already granted the Microsoft Purview managed identity
    access to our Azure Key Vault, click **Confirm**.

     ![](./media/image71.png)

9.  In the **Manage Key Vault connections** tab, click **Close**.

      ![](./media/image72.png)

10. Under **Credentials** click +**New**.

     ![](./media/image73.png)

11. Using the drop-down menu items, set the **Authentication
    method** to SQL authentication and the **Key Vault connection** to
    KeyVault01. Once the drop-down menu items are
    set, **Copy** and **paste** the values below into the matching
    fields, and then click **Create**.

      - **Name - !!credential-SQL!!**
      
      - **User name - !!sqladmin!!**
      
      - **Secret name - !!sql-secret!!**

     ![](./media/image74.png)
 
      ![](./media/image75.png)

### Task 5: Register a Source (Azure SQL DB)

1.  On the **Microsoft Purview Portal**, navigate to **Data
    map** \> **Data Sources**, and click **Register**.

     ![](./media/image76.png)

2.  Search for !!SQL Database!!, select **Azure SQL Database**, and
    click **Continue**.

      ![](./media/image77.png)

3.  Select the **Azure subscription**, **Server name
    (pvlab-RandomId-sqlsvr)**, and **Collection
    (pvlab-RandomId-pv\>Contoso)**. Click **Register**.

      ![](./media/image78.png)

### Task 6: Scan a Source with Azure Key Vault Credentials

1.  On the **Microsoft Purview Governance Portal**, navigate to **Data
    map** \> **Sources**, and within the Azure SQL Database tile, click
    the **New Scan** button.

      ![](./media/image79.png)

2.  Select your **Database** (e.g. pvlab-{randomID}-sqldb), set
    the **Credential** to **credential-SQL**, turn **Lineage
    extraction** to **Off**, and click **Test connection**. Once the
    connection test is successful, click **Continue**.

   **Note**:If the "Test connection" appears to be hanging, click Cancel and re-try.
       ![](./media/image80.png)
       ![](./media/image81.png)

3.  Click **Continue**.

     ![](./media/image82.png)

4.  Click **Continue**.

     ![](./media/image83.png)

5.  Set the trigger to **Once**, click **Continue**.

     ![](./media/image84.png)

6.  Click **Save and Run**.

      ![](./media/image85.png)

7.  To monitor the progress of the scan, click **View Details**.

      ![](./media/image86.png)

8.  Click **Refresh** to periodically update the status of the scan.

     **Note**:It will take approximately 5 to 10 minutes to complete.
 
      ![](./media/image87.png)
    
    ![](./media/image88.png)

### Task 7: View Assets

1.  On the **Microsoft Purview Governance Portal**, navigate
    to **Unified Catalog** , expand  **Discovery** and select **Data
    assets**, type the asterisk character (**\***) into the search bar,
    and hit **Enter**.

     ![](./media/image46.png)

     ![](./media/image89.png)

2.  You should be able to see a list of assets within the search
    results, which is a result of the scan.

     ![](./media/image90.png)
>
> **Summary**
>
> This lab provided an overview of how to create a collection, register
> a source, and trigger a scan.
