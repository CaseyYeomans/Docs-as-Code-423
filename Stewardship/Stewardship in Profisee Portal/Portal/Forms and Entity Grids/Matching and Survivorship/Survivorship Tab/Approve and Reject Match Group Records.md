# Approve and Reject Match Group Records

Matching strategies are designed to make the matching process easier for Data Stewards, but varying strategy thresholds and data quality can allow data from outside the ideal parameters into the match cluster. You may be required to reject or approve records manually.

Controls used:

| | |
| --- | --- |
| | **Approve** |
| | **Reject** |

To approve or reject match cluster records in FastApps Portal:

1. Open the desired match cluster. If needed, use the scroll bar to review the match cluster records.
2. To approve the record, click the **Approve** icon. The match status of the record changes from the current value to **Approved**. Any match record with a status other than Unique or Approved can be approved.
3. To reject the record, click the Reject icon. The match status of the record changes from the current value to **Rejected**.

## If Approving and Rejecting Records is Disabled

Approving or rejecting is disabled in the Match Cluster control if the Approve or Reject icon does not display. This can occur for the following reasons:

- The selected record is a golden record. Golden Records cannot be approved or rejected.
- The matching strategy is configured to disallow approval and rejection through the Web.
- The selected record is already approved. The Approve icon does not display for records that already have a status of Approved.
- The selected record is already rejected. The Reject icon does not display for records that already have a status of Rejected.
- The selected record has a status of Unique. Unique records cannot be approved or rejected.
- The record is in a group that exceeds the size supported by the Match Cluster control. The maximum size is controlled by the **Maximum match** **cluster** **size for web stewardship** system setting.
- The current user does not have permission to update the control attributes.