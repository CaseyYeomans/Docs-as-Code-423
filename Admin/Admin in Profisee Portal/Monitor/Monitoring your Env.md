# Monitoring your Environment

Profisee users can monitor all internal activities for a variety of services operating in Profisee from a single source. The Monitor tab provides an overview of processes running across the Profisee Platform, allowing users to view details for each activity.

To access the Monitor service:

1. Click the gear icon in the top-right corner of the Profisee Portal and select **Administration**.
2. Click the Monitor tab in the leftmost pane.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5d3c3e985fb08e4c.png)

From here, the Activity Monitor zone displays the following information:

- **Name**: The Name of the activity being monitored
- **Activity Type**: The Type of the activity being monitored
- **Service**: The Service that initiated the activity.
- **Status**: The Status of the activity. Includes *Running*, *Succeeded*, *Failed*, and *Timed Out*.
- **Started**: The date and time the activity was initiated.
- **Completed**: The date and time the activity finished processing. This entry is blank if it is ongoing.

To inspect a listed activity further, you can click the name of an activity or click the ellipsis icon to the left of it to open a dropdown menu. From here, you can click Open to open the Details view.

The Details view opens to the **Overview** tab. Here, you can see basic information about the service listed above as well as any activity properties.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7c36fd0f46044c77.png)

The **Details** tab displays the Process Details, including the **Code**, **Name**, and a timestamp for when the detail was added. A link may be supplied to provide additional information via [Hangfire](http://support.profisee.com/wikis/profiseeplatform/additional_monitoring_using_hangfire).![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i961d82b15432d3d8.png)