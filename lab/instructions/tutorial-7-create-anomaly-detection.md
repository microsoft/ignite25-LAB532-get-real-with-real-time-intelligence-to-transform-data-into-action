# Real-Time Intelligence tutorial part 7: Create Anomaly detection on your data

Anomaly detection is a feature of Real-Time Intelligence that allows you to identify unusual patterns in your data. In this part of the tutorial, you learn how to create an 'Anomaly detector' item on your workspace to detect anomalies in the number of empty docks at a station.

## Detect anomalies on an Eventhouse table

1. From the left navigation bar, select **Real-Time** to open the *Real-Time hub*.
2. Under **Recent streaming data** select the eventhouse table **TransformedData** you created in the previous steps. The table details page opens. Select **Detect anomalies** from the top menu.

    ![Screenshot of eventhouse table details page and detect anomalies selected.](media/detect-anomalies.png)

3. Enter **`BikeAnomaliesconfiguration`** as Name
4. Under Save to, select the workspace in which you want to create the anomaly detector item, enter a name such as **`BikeAnomalies`**. Then select **Create**.
5. In the *Select attributes* section, choose the following options:

    | Field | Value |
    | --- | --- |
    | Value to watch | No_Empty_Docks |
    | Group by | Street|
    | Timestamp | Timestamp |  

    ![Screenshot of anomaly configuration pane](media/anomaly-configuration.png)

6. Select **Run analysis**.

    > [!IMPORTANT]
    > Analysis typically takes up to 4 minutes depending on your data size and can run for up to 30 minutes. You can navigate away from the page and check back in when the analysis is complete.

    > [!NOTE]
    > Ensure your Eventhouse table contains sufficient historical data to improve model recommendations and anomaly detection accuracy. For example, datasets with one data point per day require a few months of data, while datasets with one data point per second might only need a few days.

7. When analysis is complete, anomalies along with tabular data are displayed on the right.

    ![Screenshot of completed anomaly detection](media/anomalies-detected.png)

    > [!NOTE]
    > Play around with the **Detection model** under **Customize detection** section and Timestamp above the **Detector results** pane. More data might increase anomaly detection accuracy.

8. Select **Save**.

## Create anomaly alerts

Now that you have created an anomaly detector, you can create alerts to notify you when anomalies are detected.

1. Go to Real-Time hub and select **Fabric events**.
2. Select **Set alert** on **Anomaly detection events** .

   ![Screenshot of anomaly alert selection](media/select-anomaly-alert.png) 

2. From the side **Add rule** pane, use **BikeAnomalyAlert** as the **Rule name**.
3. Under **Monitor**, click on **Select source events** and configure the following:

    | Field | Value |
    | --- | --- |
    | Event type(s) | Microsoft.Fabric.AnomalyEvents.AnomalyDetected |
    | Event scope | Select Tutorial workspace from drop down |
    | Item | Select Anomaly detector item you created in previous section **BikeAnomalies** |
    | Configuration | Select configuration you created in previous section **BikeAnomaliesconfiguration** |

    ![Screenshot of anomaly alert configuration](media/anomaly-alert-configuration.png)

4. Select **Next** and **Save**
5. Leave **Condition** as **On every value** .
6. Configure the **Action** with the following details:

    | Field | Value |
    | --- | --- |
    | Select action | Message to individuals |
    | To | Enter your email address |
    | Headline | Anomaly detected in Bike Sharing Data |
    | Notes | An anomaly has been detected in the bike sharing data. Please check. |
    | Context | Select analysisType, timestampAttributeName, timestampAttributeValue, univariate, customAttributes |

7. Configure **Save location** with the following details:

    | Field | Value |
    | --- | --- |
    | Workspace | Select Tutorial workspace from drop down |
    | Item| Create a new item |
    | New item name | AnomalyAlert |

    ![Screenshot of anomaly rule configuration](media/anomaly-rule-setup.png)

8. Select **Create** to create the anomaly alert rule.


## Next step

> Select **Next >** to create a map visualization of your anomalies.
