# Lab 05 – Creating a custom classification

Introduction

In Microsoft Purview, classifications are similar to subject tags, and
are used to mark and identify data of a specific type that's found
within your data estate during scanning. Classifications help you to
better manage your data. You can use them for prioritizing your data
efforts or improve data security and regulatory compliance.
Classifications also improve user productivity and decision-making, and
allow you to reduce costs by classifying and finding unused data.

Microsoft Purview provides a large set of default classifications that
represent typical data types that might exist in your data estate (e.g.
email address, credit card number, passport number, etc). In this module
you learn how to create a custom classification, which can be an
alternative to default classifications when they don't meet your needs.

**Objectives**

- Create a custom classification.

- Trigger a scan that will apply the custom classification to an asset.

## Task 1. Create a Classification

1.  Open the **Microsoft Purview Governance Portal**.

![](./media/image1.png)

2.  Navigate to **Data map** \> **Classifications** (under Annotation
    management) and click **+** **New**.

![](./media/image2.png)

> ![](./media/image3.png)
>
> ![](./media/image4.png)

3.  **Copy** and **paste** the values below into the appropriate fields
    and click **OK**.

> **Name - !!Twitter Handle!!**
>
> **Description - !!The username that appears at the end of your unique
> Twitter URL.!!**
>
> ![](./media/image5.png)

4.  Navigate to the **Custom** tab to confirm the custom classification
    has been created.

> ![](./media/image6.png)

## Task 2. Create a Custom Classification Rule (Regular Expression)

1.  Navigate to **Data map** \> **Classification rules** (under
    Annotation management) and click **+** **New**.

![](./media/image7.png)

2.  Populate the classification rule fields as per the example below and
    click **Continue**.

[TABLE]

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

3.  Click the **Browse** icon and open the **twitter_handles.csv** file
    from **C:\LabFiles** on your Lab VM.

> ![](./media/image9.png)
>
> ![](./media/image10.png)

4.  Select the data pattern associated to the **Handle** column and
    click **Add to patterns**.

> ![](./media/image11.png)

![](./media/image12.png)

5.  Modify the **Data Pattern** by replacing the plus symbol (+) in the
    text with **{5,15}**.

    - The plus symbol (+) indicates one or more characters matching the
      preceding item. This may lead to false positives as it would allow
      for an unlimited number of alphanumeric characters. Twitter
      handles must be a minimum of 5 and a maximum of 15 characters.

    - With {5,15}, this will ensure matches only occur where there is a
      at least 5 and at most 15 occurrences of the preceding item.

> ![](./media/image13.png)

6.  While we can also specify a **Column Pattern**, in this example we
    will rely solely on the Data Pattern. Clear the **Column
    Pattern** input and click **Create**.

![](./media/image14.png)

![A screenshot of a computer Description automatically
generated](./media/image15.png)

## Task 3 : Create a Scan Rule Set

1.  Navigate to **Data map** \> **Scan rule sets** (under Source
    management) and click **+ New**.

![](./media/image16.png)

2.  Change the **Source Type** to **Azure Data Lake Storage
    Gen2** then **copy** and **paste** the values below into the
    appropriate fields. Click **Continue**.

> **Scan rule set name - !!twitter_scan_rule_set!!**
>
> **Scan rule description - !!Custom scan rule set to detect parquet
> files and classify twitter handles.!!**
>
> ![](./media/image17.png)

3.  Clear all file type selections except for **PARQUET** and
    click **Continue**.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

4.  Clear all selected **System rules** and select the custom
    classification rule **twitter_handle** and click **Continue**.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

5.  Click **Create**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

## Task 4: Upload Data to an Azure Data Lake Storage Gen2 Account

1.  Navigate to the **Home** tab of Azure portal and select **All
    resources**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image21.png)

2.  Select your **Azure Data Lake Storage Gen2 account**
    (e.g. pvlab{randomId}adls).

> ![A screenshot of a computer Description automatically generated with
> medium confidence](./media/image22.png)

3.  In the Azure Data Lake in the Overview page. In the left-side
    navigation pane, navigate to **Data storage** section, then click on
    **Containers**, select **raw** container**.**

> ![](./media/image23.png)

4.  On **raw** container page, click on **Upload** button.

> ![](./media/image24.png)

5.  In the **Upload blob** pane, click on **Browse for file**, navigate
    to **C:\Labfiles** location and select **twitter_handles.parquet**,
    then click on the **Open** button.

> ![](./media/image25.png)
>
> ![](./media/image26.png)

6.  In the **Upload blob** pane, drop down the Advanced, enter
    !!**Twitter!!** as **Upload to folder** and click on **Upload**

> ![](./media/image27.png)

![](./media/image28.png)

## Task 5:  Scan an Azure Data Lake Storage Gen2 Account

1.  Open the **Microsoft Purview Governance Portal**, navigate to **Data
    map** \>** Data Sources** and click **New Scan** within the **Azure
    Data Lake Storage Gen2** tile.

![](./media/image29.png)

> ![](./media/image30.png)

2.  Click **Test connection** to ensure the credentials have access and
    click **Continue**.

> ![](./media/image31.png)

3.  By default, Microsoft Purview will have the parent Azure Data Lake
    Storage Gen2 account selected and therefore include all paths in
    scope. To reduce the scope, deselect the parent and select
    the **Twitter** folder only. Click **Continue**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

4.  To validate the scope of the custom scan rule set, click **View
    detail**.

![A screenshot of a computer program Description automatically
generated](./media/image33.png)

5.  Confirm that the custom scan rule set includes the **PARQUET** file
    type and the custom classification rule **twitter_handle**.
    Click **OK**.

> ![](./media/image34.png)

6.  Select the custom scan rule set **twitter_scan_rule_set** and
    click **Continue**.

![A screenshot of a scan rule Description automatically
generated](./media/image35.png)

7.  Set the scan trigger to **Once** and click **Continue**.

![A screenshot of a computer screen Description automatically
generated](./media/image36.png)

8.  Click **Save and Run**.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

9.  To view the progress of the scan, navigate to **Sources** and
    click **View details** on the **Azure Data Lake Storage Gen2** tile.

![](./media/image38.png)

10. Periodically click **Refresh** to update the scan status
    until **Complete**.

> ***Note***
>
> *This will take approximately 5 to 10 minutes.*
>
> ![](./media/image39.png)
>
> ![](./media/image40.png)

## Task 6: Search by Classification

1.  On the **Microsoft Purview Governance Portal**, navigate
    to **Unified Catalog** , expand  **Discovery** and select **Data
    assets**, type the asterisk character (**\***) into the search bar,
    and hit **Enter**.

> ![](./media/image41.png)

2.  Limit the search results by setting **Classification** within the
    filter panel to **Twitter Handle**. Click on the asset title
    (**twitter_handles.parquet**) to view the asset details.

> ![](./media/image42.png)

3.  You will notice on the **Overview** tab that the schema includes the
    **Twitter Handle classification**. To identify which column has been
    classified, navigate to the **Schema** tab.

> ![](./media/image43.png)

4.  Within the **Schema** tab we can see that **Account name** is the
    column that has been classified.

![](./media/image44.png)

**Summary**

This lab provided an overview of how to create a custom classification,
and how to have the classification automatically applied as part of a
scan using a custom scan rule set.
