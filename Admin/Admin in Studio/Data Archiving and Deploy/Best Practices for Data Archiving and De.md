# Best Practices for Data Archiving and Deployment

- When possible, initiate both archiving and deployment on a client installed on a different computer than the Profisee server. Using separate systems increases the amount of resources available to complete the processes.
- Confirm that the Profisee server has adequate CPU processing power available when processing an archiving strategy, as this process is very CPU-intensive. Archiving has little effect on the client.
- Confirm that the client computer has sufficient memory available when deploying an archive. Deployment is a memory-intensive process on the client.
- Avoid performing resource-intensive, long-running tasks such as matching or address verification during archiving.
- Use the Data Archiving setting under FastApps Studio Settings to control the maximum number of cores used for archiving on the client computer. By default, the **Maximum number of cores** setting is 1. If you have more than two available cores, you can change this setting to improve performance.

Use this formula to determine the number of cores to use:

**Maximum number of cores = Total available client cores - 2**
- The FastApps Studio Settings configuration does not affect command line procedures. Be sure to use the correct switches to set the batch size and the maximum number of cores when using command line options.
- The **Publish Batch Size Desktop** setting on the **Entity** tab is set to 1000 by default, which is ideal for importing smaller volumes directly into the entity grid. However, if you are loading records via Data Deployment, a batch size of 10,000 is recommended.