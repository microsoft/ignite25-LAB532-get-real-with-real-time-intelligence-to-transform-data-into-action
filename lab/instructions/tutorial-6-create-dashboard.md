# Real-Time Intelligence tutorial part 5: Create a Real-Time dashboard

In this part of the tutorial, you learn how to create a Real-Time Dashboard in Real-Time Intelligence. You create a Kusto Query Language (KQL) query, create a Real-Time Dashboard, add a new tile to the dashboard, and explore the data visually by adding an aggregation.

## Create a Real-Time dashboard

1. In your KQL queryset, copy/paste, and run the following query. This query might already have been run from the previous section in this tutorial. This query returns a column chart showing the most recent number of bikes by *BikepointID*.

    ```kusto
    AggregatedData 
    | sort by BikepointID 
    | render columnchart with (ycolumns=No_Bikes, xcolumn=BikepointID)
    ```

    ![Screenshot of query showing column chart of bikes by bike point ID.](media/bikes-by-bikepoint.png)

2. Select **Save to dashboard** and **New Real-Time Dashboard**.
3. Enter the following information:

    ![Screenshot of pinning query to dashboard in Real-Time Intelligence.](media/pin-dashboard.png)

    | Field | Value |
    | --- | --- |
    | **Dashboard name** | +++*TutorialDashboard*+++ |
    | **Tile name** | +++*Recent bikes by Timepoint*+++ |
    | **Open dashboard after creation** | *Selected* |

4. Select **Create**.

Since you've selected **Open dashboard after creation**, the new Real-Time dashboard, *TutorialDashboard*, opens with the *Recent bikes by Bikepoint* tile. You can also access the Real-Time dashboard by browsing to your workspace and selecting the desired item.

## Add a new tile to the dashboard

1. On the top menu bar, toggle from **Viewing** mode to **Editing** mode.
2. Select **New tile**

    ![Screenshot of Real-Time dashboard in editing mode with new tile selected.](media/new-tile.png)

3. In the query editor, enter and run the following query:

    ```kusto
    RawData
    | where Timestamp > ago(1h)
    ```

4. Above the results pane, select **+ Add visual**.
5. In the **Visual formatting** pane, enter the following information:

    | Field | Value |
    | --- | --- |
    | Tile name | *`Bike locations Map`* |
    | **Visual type** | *Map* |
    | **Define location by** | *Latitude and longitude* |
    | **Latitude column** | *Latitude* |
    | **Longitude column** | *Longitude* |
    | **Label column** | *BikepointID* |

6. Select **Apply changes**.
    You can resize the tiles and zoom in on the map as desired.

    ![Screenshot of Real-Time dashboard in editing mode with map tile added.](media/final-dashboard.png)

7. Save the dashboard by selecting the **Save** icon on the top left corner of the dashboard.

## Next step

> Select **Next >** to set an alert on your event stream
