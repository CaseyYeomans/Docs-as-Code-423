# Match Group Visualizer

The Match Group Visualizer is a view within the Match Group Control that allows the user to see a high-level structure of the group and view all details that cause records to match into a group. Within the Match Group Visualizer, a user can survive, promote and harmonize, and manage the data and status of records within the group. You can also split and combine records to and from the group.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iea181d5f91def043.png)

To access to the Match Group Visualizer:

- Open your instance of Profisee FastApp Portal.
- Open the match group you want to view in the vizualizer.
- Select the **Visualizer**tab in the top-right corner of the match group window.

The Match Group Visualizer contains a graph of the group composed of nodes that represent the group's members. Each node contains a color-coded header to represent the record's match status, along with the record's name and match score. Each node contains an arrow or set of arrows that shows how it is related to other nodes within the match group.

| | |
| --- | --- |
| - An edge with a single arrow indicates that the node at the start of the arrow matched to the node at the end of the arrow. The score on the starting node is the score relative to the ending node. | |
| - An edge with a double arrow indicates that the nodes on each end of the arrow matched to each other. Such a node pair will form an island within the group. Each node's score is relative to its partner in the relationship. The Match Member attributes in the pair point to each other. | |
| - A node with no inbound or outbound arrows represents a record that was either (a) forced into the group through a user-mapping process or (b) is a **golden record** that was created by the match strategy as part of the survivorship process. |