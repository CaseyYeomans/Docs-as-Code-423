# Microsoft Workflow Foundation

The Profisee Platform's Workflow services leverage the capabilities of the .NET Framework's Workflow Foundation classes and tools. These capabilities allow you to construct and manage long-running workflows that support your data management solutions. This article provides a brief overview of the capabilities of Workflow Foundation along with helpful links to get you started on building workflows for the Profisee Platform.

### What is Windows Workflow Foundation

**Workflow Foundation (WF)**, pronounced "dub-F", provides a collection of design-time and runtime capabilities that support a variety of process-oriented scenarios. Profisee leverages these within our Workflow Services subsystem to support long-running processes that assist in managing your data. WF provides the following capabilities that are leveraged by the Profisee Platform:

- A design and authoring capability based on XAML (Extensible Application Markup Language) that allows you to define a collection of Activities that collectively implement a process.
- Runtime services that control the lifecycle of instances of each process - starting, suspending, resuming, tracking, and stopping.
- Data services that support the ability to store the state of instances while they are suspended, allowing them to be resumed later when events trigger further actions on those instances.

At a simple level, a workflow is a collection of **activities** that are arranged on the design surface as you would arrange a typical flow chart or process diagram. Activities exist in a variety of categories such as:

- Primitives, such as assignments
- Control flow, including if-then-else, loops, sequences, parallel paths, etc.
- Error handling, such as throwing and catching exceptions
- Runtime services, such as terminating the current workflow

WF's standard activities are included in the **System.Activities** namespace of the .NET Framework assemblies. The figure below illustrates the structure of a basic workflow as it would appear on the design surface within Visual Studio. Activities are represented by the various boxes. Some activities such as a **Sequence** (e.g. Main Sequence), **Pick**, and **PickBranch** may contain other activities.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic4aeccc8af0a8b6a.png)

The Profisee Software Developers Kit (SDK) provides a collection of activities that can be added to the workflow design surface that allow your workflows to interact with Profisee's platform services. For example, the figure above contains the following Profisee SDK activities: **InitiateWorkflow**, **GetRecord**, **ContributionTask**, and **ApprovalTask**.

For more details, refer to the [Workflow Activities](https://support.profisee.com/wikis/profiseeplatform/workflow_activities_overview) and [Build a Workflow with Visual Studio](https://support.profisee.com/wikis/profiseeplatform/build_a_workflow_with_visual_studio) help articles. For in depth information on Microsoft Windows Workflow Foundation, refer to the links under *See Also* below.

### See Also

[Getting Started Tutorial](https://docs.microsoft.com/en-us/dotnet/framework/windows-workflow-foundation/getting-started-tutorial)

[Windows Workflow Foundation Programming](https://docs.microsoft.com/en-us/dotnet/framework/windows-workflow-foundation/programming)

[Designing Workflows](https://docs.microsoft.com/en-us/dotnet/framework/windows-workflow-foundation/designing-workflows)

[Guide to the Windows Workflow Documentation](https://docs.microsoft.com/en-us/dotnet/framework/windows-workflow-foundation/guide-to-the-documentation)