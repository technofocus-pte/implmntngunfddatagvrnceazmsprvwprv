# Lab 3 - Search the Microsoft Purview Data Catalog

**Introduction**

In this lab, you'll learn to edit technical metadata by adding
definitions and classifications to data attributes, such as tables and
columns. You'll learn to assign technical ownership by linking technical
attributes to contact persons. You'll learn to use classifications to
mark data. All these activities, such as categorizing data, will help
you to better manage your data.

**Objectives**

- Create a collection.

- Register and scan an Azure Data Lake Storage Gen2 account using the
  Microsoft Purview managed identity.

## Task 1. Search Catalog

1.  Navigate to the **Home** tab of Azure portal and select **All
    resources**.

> ![A screenshot of a computer Description automatically generated with
> medium confidence](./media/image1.png)

2.  Open the **Microsoft Purview account** **(pvlab-RandomId-pv)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Navigate to your ***Microsoft Purview account***
    **(pvlab-{*randomId*}-pv)** and click the **Open Microsoft Purview
    Governance Portal** tile.

> ![](./media/image3.png)

4.  On the **Microsoft Purview Governance Portal**, navigate
    to **Unified Catalog** , expand  **Discovery** and select **Data
    assets**, type the asterisk character (**\***) into the search bar,
    and hit **Enter**.

> ![](./media/image4.png)

5.  Filter the search results
    by **Classification** (e.g. **Country/Region**) and click the
    hyperlinked asset name to view the details (e.g. QueriesByState).

> ![](./media/image5.png)
>
> ![](./media/image6.png)

## Task 2. Update an Asset

1.  In the **QueriesByState** tab, click **Edit** to modify the asset
    details.

> ![](./media/image7.png)

2.  Update the **Description** by copying and pasting the sample text
    below.

> !!This dataset was curated from the Bing search logs (desktop users
> only) over the period of Jan 1st, 2020 – (Current Month - 1). Only
> searches that were issued many times by multiple users were included.
> The dataset includes queries from all over the world that had an
> intent related to the Coronavirus or Covid-19. In some cases this
> intent is explicit in the query itself (e.g., “Coronavirus updates
> Seattle”), in other cases it is implicit , e.g. “Shelter in place”!!

3.  Assign a **Classification** (e.g. World Cities) using the drop-down
    menu.

> ![](./media/image8.png)

4.  Navigate to the **Schema** tab and update the **Asset
    description** for each column using the sample text below.

> **Date**
>
> !!Date on which the query was issued.!!
>
> **Query**
>
> !!The actual search query issued by user(s).!!
>
> **IsImplicitIntent**
>
> !!True if query did not mention covid or coronavirus or sarsncov2
> (e.g, “Shelter in place”). False otherwise.!!
>
> **State**
>
> !!State from where the query was issued.!!
>
> **Country**
>
> !!Country from where the query was issued.!!
>
> **PopularityScore**
>
> !!Value between 1 and 100 inclusive. 1 indicates least popular query
> on the day/State/Country with Coronavirus intent, and 100 indicates
> the most popular query for the same geography on the same day.!!
>
> ![](./media/image9.png)
>
> ![](./media/image10.png)

5.  Navigate to the **Contacts** tab and set someone within your
    organization to be an **Expert** and an **Owner** (Provide Tenant
    email-ID). Click **Save**.

6.  For assets in which you are tagged as a **Contact**, these will
    appear on the home screen (Data catalog), under **My items**.

![](./media/image11.png)

7.  To see other assets within the same path, navigate to
    the **Related** tab.

> ![](./media/image12.png)

## Task 3: Browse the catalog by source

While the search experience is ideal for keyword based discovery, the
Microsoft Purview Governance Portal allows alternate methods of browsing
assets (i.e. by collection OR by source type).

1.  On the **Microsoft Purview Governance Portal**, navigate
    to **Unified Catalog** and select **Data assets under Discovery.** 

> ![](./media/image13.png)

2.  In the Data assets tab, select **Explore by source type** tile .![A
    screenshot of a computer Description automatically
    generated](./media/image13.png)

3.  Switch to the **Browse** **by source type** tab and select
    a **source** as **Azure Data Lake Storage Gen2**.

> ![](./media/image14.png)

![A screenshot of a computer Description automatically
generated](./media/image15.png)

4.  Select the **pvlab{randomId}adls** storageaccount 

![](./media/image16.png)

5.  Under the storage, Select the **raw** container 

![](./media/image17.png)

> ![](./media/image18.png)

## Task 4: Perform a Bulk Edit option

Microsoft Purview allows us to perform certain operations
(add/replace/remove) against a subset of attributes (Expert, Owner,
Term, Classification) in bulk directly within the Microsoft Purview
Governance Portal.

1.  On the **Microsoft Purview Governance Portal**, navigate
    to **Unified Catalog** , expand  **Discovery** and select **Data
    assets**, type the asterisk character (**\***) into the search bar,
    and hit **Enter**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

2.  On the **Data catalog** pane , under **Asset Type** select the
    **Data** and select  **File** and **Table**. select the first five
    items in the search results, and click **View selected**.

> ![](./media/image19.png)

![](./media/image20.png)

3.  On the **Select assets** tab , Click **Bulk edit**.

> ![](./media/image21.png)

4.  Set the **Attribute** to **Owner**, set **Operation** to **Add**,
    select your **Tenant** **user** for New value, and click **Apply**.

![](./media/image22.png)

5.  On the **Select assets** tab, Click **Deselect all and close**.

![](./media/image23.png)

**Summary**

This lab provided an overview of how to search, browse, and update
assets.
