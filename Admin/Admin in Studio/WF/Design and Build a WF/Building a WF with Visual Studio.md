# Building a Workflow with Visual Studio

Before a user can administer a workflow in FastApp Studio, the workflow must be developed using Visual Studio and the Profisee SDK Workflow Tools. To make the process as user-friendly as possible, the Profisee SDK includes a Visual Studio project template available through the Profisee SDK Visual Studio extension. Additionally, a suite of workflow activities is available through toolbox controls when designing a workflow. Refer to the [Workflow Activities](https://support.profisee.com/wikis/profiseeplatform/workflow_activities_overview)section of this documentation for detailed descriptions and use-cases for the included activities.

**As of version 2022.R2 and onward,**anything that makes use of the SDK must include references to:

- System.ServiceModel.NetTcp
- System.ServiceModel.Http
- System.ComponentModel.Annotations

All of which can be found within the *AcceleratorFramework* install folder.

## Creating a New Workflow

1. **Create a New Project** in Visual Studio from **Profisee Workflow Library**.
2. Configure the project name, location directory, solution name, and framework for your project.

The solution includes a default project which contains the required References and two sample .xaml files for basic workflows. Profisee workflows are defined in .xaml file format. When you register a workflow in Profisee FastApp Studio, you select the .xaml file associated with a workflow project to register that workflow.

To change the Workflow name, select the **Properties** tab in the bottom-right corner of the screen, then select the **Name** text box in the top-right.

4. Click **Create**.
5. Expand the project under Solution Explorer and double click the xaml file to open the sample workflow in the workflow designer.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i71aae78941e30d18.png)

In this sample .xaml, you will see a pre-built workflow template in the workflow designer. This workflow contains a sequence of activities for a basic workflow: InitiateWorkflow, ContributionTask, and ApprovalTask activities with their appropriate properties filled out. This is a basic workflow that is ready to use as is, and might only require the specification of the appropriate entity name in the InitiateWorkflow activity. You may also use this as a starting point and change or add activities to create your own workflow logic. Note that the InitiateWorkflow task must be included as the first activity in the sequence to properly execute a workflow.

Additionally, the **Profisee Template Workflow Activity**pre-built workflow template contains the same activities as above, but the InitiateWorkflow activity is replaced with the similar InitiateTemplateWorkflow activity. This activity does not require you to define an entity. You will be able to define one or more entities during the [configuration](https://support.profisee.com/wikis/profiseeplatform/configuring_workflows) process.

6. Design your workflow by dragging activities or controls from the provided workflow sections in the toolbox into the workflow designer, then setting all required in-argument or out-argument values. ![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i1354c55628c715b.png)

- Drag workflow activities into the designer in the order in which you want the activities to occur. The downward-facing arrow indicates that one activity will trigger the next. If you want workflow activities to run in a non-linear fashion, refer to [Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/jj684582.aspx) documentation for more information on using the default workflow tools in Visual Studio.
- Satisfy the argument values within the activities in the workflow designer. Refer to the [Workflow Activities](https://support.profisee.com/wikis/profiseeplatform/workflow_activities_overview) section of this documentation for more information on argument values for specific activities.
- Satisfy the required properties of each activity in the Properties field. Some of these properties may be others while others are required. Refer to the [Workflow Activities](https://support.profisee.com/wikis/profiseeplatform/workflow_activities_overview) section of this documentation for more information about workflow properties for specific activities.

If needed, you can add another .xaml using the template to create a new workflow under the same project by right-clicking the project name within the Solution Explorer panel, then clicking **Add** > **New Item** > **Workflow** > **Profisee Workflow Activity**.

7. Click **Build** on the topmost toolbar, then select **Build Solution**.

The Output panel will display the build process in real time and display errors if any are encountered. All errors must be addressed before the project can be successfully built.

Once the project has been successfully built, you can [r](https://support.profisee.com/wikis/profiseeplatform/registering_workflows)[egister any of the Profisee workflows](http://support.profisee.com/wikis/profiseeplatform/registering_workflows) within the project in Profisee FastApp Studio to begin administering the workflow.