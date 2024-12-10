# Lab 06 – Lineage between datasets created by data processes

**Introduction**

One of the features of Microsoft Purview is the ability to show the
lineage between datasets created by data processes. Data lineage shows
how data moves over time and enables you to see how data is used and
what changes to data have been made. This visibility helps you to
understand, trace back and correct data at the source of origin.
Lineage, thus also results into better data quality.

Lineage is typically captured from tools that extract, transform and
load data. These ETL tools are, for example, Data Factory, Data Share,
and Power BI. They capture the lineage of data as it moves. By scanning
these ETL tools you can capture and visualize the lineage in Microsoft
Purview.

Microsoft Purview also supports the ability to document custom lineage.
Custom lineage is lineage that you created yourself, for example by
uploading metadata using the Microsoft Purview's Atlas REST APIs, or by
adding manual lineage via the Microsoft Purview governance portal.
Lineage in Purview includes relationships between datasets and
processes**.**

**Objectives**

- Connect an Azure Data Factory account with a Microsoft Purview
  account.

- Trigger a Data Factory pipeline to run so that the lineage metadata
  can be pushed into Purview.

## Task 1 :Create an Azure Data Factory Connection in Microsoft Purview

1.  Open the **Microsoft Purview Governance Portal**.

    ![](./media/image1.png)

2.  Navigate to **Data Map,** dropdown the **Source management** and
    select **Lineage connection**.

      ![](./media/image2.png)

3.  In **Lineage connections** pane, select **Data Factory** and select
    **+New**

  ![](./media/image3.png)
 
    ⚠️ To view/add/remove Data Factory connections, you need to be
    assigned the **Collection admin** role on the root collection.

4.  Select your **Azure Subscription**. Select your **Azure Data
    Factory** account instance from the drop-down menu
    (e.g. pvlab-{randomId}-adf) and click **OK**.

      ![](./media/image4.png)

5.  Once finished, you should see the Data Factory in
    a **connected** state.

      ![](./media/image5.png)

6.  To confirm that Azure Data Factory has been provided the necessary
    access, navigate to **Data
    map** \> **Domains** \>** pvlab-RandomId-pv \> Contoso** \> **Role
    assignments**, within **Data curators** you should be able to see
    the Azure Data Factory managed identity.

    ![](./media/image6.png)

    ![](./media/image7.png)

## Task 2: Copy Data using Azure Data Factory Studio.

1.  Navigate to the **Home** tab of Azure portal and select **All
    resources**.

     ![](./media/image8.png)

2.  Switch to the **Azure Portal** tab and navigate to your **Azure Data
    Factory** resource (pvlab-{randomId}-adf).

     ![](./media/image9.png)

3.  Click **Launch Studio** on the **Azure Data Factory Overview** page.

     ![](./media/image10.png)

4.  Click **Ingest**.

     ![](./media/image11.png)

5.  Select **Built-in copy task** and then click **Next**.

      ![](./media/image12.png)

6.  Change the **Source type** to **Azure Data Lake Storage Gen2** and
    then click **+ New connection**.

      ![](./media/image13.png)

7.  Select your **Azure subscription** and **Storage
    account** (e.g. pvlab{randomId}adls), click **Test connection** and
    then click **Create**.

    ![](./media/image14.png)
  
    ![](./media/image15.png)

8.  In the Source data store pane, click **Browse**.

      ![](./media/image16.png)

9.  Navigate to **raw \> 2020** and click **OK**.

    ![](./media/image17.png)

10. Confirm your folder path selection and click **Next**.

    ![](./media/image18.png)

11. Preview the sample data by clicking **Preview data**, and then
    click **Next**.

    ![](./media/image19.png)

12. Change the **Destination type** to **Azure Data Lake Storage Gen2**,
    set the **Connection** to the existing connection
    (e.g. AzureDataLakeStorage1), and then click **Browse**.

    ![](./media/image20.png)

13. Navigate to raw/ and click **OK**.

    ![](./media/image21.png)

14. Confirm your folder path selection, set the **file
    name** to **2020_merged.parquet**, set the **copy
    behavior** to **Merge files**, and click **Next**.

    ![](./media/image22.png)

15. Set the **file format** to **Parquet format** and click **Next**.

    ![](./media/image23.png)

16. Leave the default settings and click **Next**.

    ![](./media/image24.png)

17. Review the summary and proceed by clicking **Next**.

     ![](./media/image25.png)

18. Once the deployment is complete, click **Finish**.

      ![](./media/image26.png)

19. Navigate to the **Monitoring** screen to confirm the **pipeline**
    has run **successfully**.

     ![](./media/image27.png)

## Task 3: View Lineage in Microsoft Purview

1.  Navigate to the **Microsoft Purview Governance Portal**, from the
    **Unified catalog** screen select Data assets and click **Explore by
    source type**.

      ![](./media/image28.png)

2.  Switch to the **By source type** tab and then select **Azure Data
    Factory**.

      ![](./media/image29.png)

3.  Select the **Azure Data Factory account
    instance** (e.g. pvlab-{randomId}-adf).

      ![](./media/image30.png)

4.  Select the **Copy Pipeline** and click to open the **Copy
    Activity**.

    ![](./media/image31.png)
   
    ![](./media/image32.png)

5.  Navigate to the **Lineage** tab.

    ![](./media/image33.png)

6.  You can see the lineage information has been automatically pushed
    from Azure Data Factory to Purview. On the left are the two sets of
    files that share a common schema in the source folder, the copy
    activity sits in the center, and the output file sits on the right.

    ![](./media/image34.png)

**Summary**

This module provided an overview of how to integrate Microsoft Purview
with Azure Data Factory and how relationships between assets and ETL
activities can be automatically created at run time, allowing us to
visually represent data lineage and trace upstream and downstream
dependencies.
