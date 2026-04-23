# Install Subscribers On the Event Consuming Server

## Installing

Subscribers are plug-in event handlers (DLLs and supporting files) for processing events.

By default, the subscriber folder is located here:

\\[Your File Repository]\Profisee\Subscribers

This directory is initially empty for a newly installed Profisee server node. You must first copy the subscriber files to this directory to install them, and then [register them](https://support.profisee.com/wikis/profiseeplatform/register_a_subscriber) in a separate step to use them with event processing.

Subscribers may be licensed software, delivered by Profisee, or custom software, created by customers or third parties. The plug-in approach makes it possible for Profisee to deliver subscribers separately, as new subscriber releases may be available more frequently than Profisee releases. Some subscribers are available with the Integrator (formerly Federation Manager) installation; other subscribers are available for download at [www.profisee.com](http://www.profisee.com/) (accessible with your customer login).

After you have obtained one or more valid subscriber files, you can install them manually by copying them to the Subscribers directory on the Profisee server.

The Subscribers directory will initially contain the file Profisee.Services.Sdk.Server.WorkflowSubscriber.dll, which is the Workflow subscriber. Be sure to keep this file when you copy files in the Subscribers directory from Integrator.

## Integrator and the Data Transfer Controller

Profisee (R) Integrator ships with two subscribers: the Data Transfer Controller and the Data Service Controller.

The Data Transfer Controller and supporting connectors enable the creation of data integration scenarios. The Data Service Controller supports connectors allowing enrichment of Profisee data by Web-based service providers.

Each release of Integrator includes the latest Data Transfer Controller, Data Service Controller, and available connectors. You do not need to download these files separately. Additional connectors may be released between Integrator releases, and these files can be licensed through Profisee and downloaded through Profisee.com.

When Integrator is installed, the subscribers (Data Transfer Controller and Data Service Controller) and related connector files are installed in the Integrator location.

By default, the subscriber files are located here:

C:\Program Files\Profisee\Master Data Maestro Integrator\*versionNumber*\Subscribers

Manually copy the complete contents of this folder (including subfolders) to the Profisee Server location:

\\[Your File Repository]\Profisee\Subscribers

## Multiple Server Nodes in a Cluster

For clusters with server roles that are distributed among different nodes:

Subscribers are installed on one or more specific nodes within a multi-node server cluster. After assigning the Event Consuming role to one or more Profisee server nodes, manually copy the Subscribers folder to those servers in the cluster.

## Upgrading

When upgrading a subscriber or a connector file on Profisee Server, be sure to stop event processing before copying the new file to the folder. You will also need to stop and restart the Profisee service to update the subscriber and connector in memory.

You may need to delete existing connector files before installing new versions of connectors because the file name may have changed. Refer to specific upgrade information for that connector in the release notes and the user guide.

After upgrading a subscriber that is already registered, go to the Subscribers tab in Event Processing and click **Save**. This writes any changes or new options in the subscriber to the database.