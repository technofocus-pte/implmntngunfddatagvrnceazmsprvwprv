# Lab 06 – Lineage between datasets created by data processes

### **Task 1 :Create an Azure Data Factory Connection in Microsoft Purview**

1.  Open the **Microsoft Purview Governance Portal**.

![](./media/image1.png)

2.  Navigate to **Management** \> **Data Factory** (under Lineage
    connections) and click **+ New**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

> ⚠️ To view/add/remove Data Factory connections, you need to be
> assigned the **Collection admin** role on the root collection.

3.  Select your **Azure Subscription**. Select your **Azure Data
    Factory** account instance from the drop-down menu
    (e.g. pvlab-{randomId}-adf) and click **OK**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  Once finished, you should see the Data Factory in
    a **connected** state.

![A screen shot of a computer Description automatically
generated](./media/image4.png)

5.  To confirm that Azure Data Factory has been provided the necessary
    access, navigate to **Data
    map** \> **Domains** \>** pvlab-RandomId-pv \> Contoso** \> **Role
    assignments**, within **Data curators** you should be able to see
    the Azure Data Factory managed identity.

![](./media/image5.png)

### **Task 2: Copy Data using Azure Data Factory Studio.**

1.  Navigate to the **Home** tab of Azure portal and select **All
    resources**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image6.png)

2.  Switch to the **Azure Portal** tab and navigate to your **Azure Data
    Factory** resource (pvlab-{randomId}-adf).

![A screenshot of a computer Description automatically
generated](./media/image7.png)

3.  Click **Launch Studio** on the **Azure Data Factory Overview** page.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

4.  Click **Ingest**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

5.  Select **Built-in copy task** and then click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

6.  Change the **Source type** to **Azure Data Lake Storage Gen2** and
    then click **+ New connection**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

7.  Select your **Azure subscription** and **Storage
    account** (e.g. pvlab{randomId}adls), click **Test connection** and
    then click **Create**.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

8.  Click **Browse**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

9.  Navigate to **raw \> BingCoronavirusQuerySet \> 2020** and
    click **OK**.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

10. Confirm your folder path selection and click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

11. Preview the sample data by clicking **Preview data**, and then
    click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

12. Change the **Destination type** to **Azure Data Lake Storage Gen2**,
    set the **Connection** to the existing connection
    (e.g. AzureDataLakeStorage1), and then click **Browse**.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

13. Navigate to raw/ and click **OK**.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

14. Confirm your folder path selection, set the **file
    name** to **2020_merged.parquet**, set the **copy
    behavior** to **Merge files**, and click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

15. Set the **file format** to **Parquet format** and click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

16. Leave the default settings and click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

17. Review the summary and proceed by clicking **Next**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

18. Once the deployment is complete, click **Finish**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

19. Navigate to the **Monitoring** screen to confirm the pipeline has
    run **successfully**.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

### **Task 3: View Lineage in Microsoft Purview**

1.  Navigate to the **Microsoft Purview Governance Portal**, from
    the **Data catalog** screen click **Browse**.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

2.  Switch to the **By source type** tab and then select **Azure Data
    Factory**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

3.  Select the **Azure Data Factory account
    instance** (e.g. pvlab-{randomId}-adf).

![A screenshot of a computer Description automatically
generated](./media/image27.png)

4.  Select the **Copy Pipeline** and click to open the **Copy
    Activity**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

5.  Navigate to the **Lineage** tab.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

6.  You can see the lineage information has been automatically pushed
    from Azure Data Factory to Purview. On the left are the two sets of
    files that share a common schema in the source folder, the copy
    activity sits in the center, and the output file sits on the right.

![A screenshot of a computer Description automatically
generated](./media/image30.png)
