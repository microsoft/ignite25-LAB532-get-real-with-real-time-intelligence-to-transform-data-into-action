# Real-Time Intelligence tutorial part 3: Set an alert on your event stream

The event stream insights are now available for you to create alerts. In this part of the tutorial, you learn how to set an alert on your event stream to receive a notification in Teams when the number of bikes falls below a certain threshold.

## Set an alert on the event stream

1. From the left navigation bar, select **Real-Time** to open the *Real-Time hub*.
2. Under **Recent streaming data** select the event stream you created in the previous tutorial named *TutorialEventstream*.
    The event stream details page opens.

    ![Screenshot of event streams details page and set alert selected.](media/set-alert.png)

3. Select **Set alert**
4. A new pane opens. Enter **`TutorialRule`** in the **Rule name** field. Fill in the fields as follows:

    | Field | Value |
    | --- | --- |
    | **Condition** |  |
    | Check | On each event when |
    | Field | No_Bikes |  
    | Condition | Is less than |
    | Value | 5 |
    | **Action** |  **Message to individuals** |
    | **Save location** | |
    | Workspace | The workspace in which you created resources|
    | Item | Create a new item |
    | New item name | *`TutorialRule`* |

    ![Screenshot of Set alert pane in Real-Time Intelligence.](media/alert-logic.png)

5. Select **Create** then select **Done**.

## Next step

> Select **Next >** to transform data in a KQL database.
