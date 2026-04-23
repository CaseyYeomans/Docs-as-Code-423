# Quick Start Guide

The Profisee Platform is a powerful Master Data Management (MDM) tool with a wide variety of features and capabilities. If you are new to MDM, a fresh installation of Profisee FastApp Studio or a blank FastApp Portal page may seem intimidating and overwhelming. However, getting started is much more simple than it may appear, and a workday's worth of setup can turn an empty platform into a powerful and intuitive tool.

This guide details the four major steps that must be taken before the Profisee Platform can be used to its full potential.

- Installing the Platform
- Creating a Model
- Inserting data into FastApp Studio
- Creating a Portal page

Once you have finished these five steps, your instance of the Profisee Platform is ready for use.

This guide includes information for getting started with Profisee FastApp Studio and Profisee FastApp Portal. If your instance requires work with auxiliary software such as [Profisee Integrator](https://support.profisee.com/wikis/profiseeplatform/Before_you_begin) or the [Profisee REST API](https://support.profisee.com/wikis/profiseeplatform/profisee_rest_api_overview), refer to the documentation for those tools specifically.

## Installing the Platform

Before anything else can be done, you must install the Profisee Platform. There are several methods of installing the platform, but regardless of which you choose, you must provide a set of credentials including your Profisee license, user name, and password.

### Obtaining Your Profisee License and Credentials (If required)

If you are performing an on-prem installation, you only need the Profisee license supplied to you by Profisee support. However, for PaaS installations of the Profisee server, you may need additional credentials to finish installation. You must do the following to create and use your Profisee credentials:

1. Navigate to the [Profisee Support](http://support.profisee.com/aspx/CustomerHome) portal and click [Support](https://support.profisee.com/Force/force__case/index) on the header toolbar.
2. Open a new ticket and select "I have a license question" as the Case Reason.
3. Provide Profisee support with the DNS URL for the environment you are creating.
This URL must match the one that you will use for the platform, and should be given in the format: *https://server.domain.com*.
4. Save the credentials received from customer support.

### Navigating the Installation Process

Once you have obtained your credentials, you should install the Profisee Platform. The Profisee Platform can be installed using one of three methods. Refer to the following installation guides for each of the three installation methods to navigate the installation process.

- [On-prem installation using Configuration Manager](https://support.profisee.com/wikis/profiseeplatform/installation_guide_overview)
- [Platform as a Service (PaaS) Deployment using Profisee's Azure Kubernetes Services (AKS)](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template)
- [Platform as a Service (PaaS) Deployment using Amazon Web Services (AWS)](https://support.profisee.com/wikis/profiseeplatform/profisee_aws_deployment_overview)

Regardless of the installation process, you should now have access to Profisee FastApp Studio, Profisee FastApp Portal, and the [Profisee REST API](https://support.profisee.com/wikis/profiseeplatform/profisee_rest_api_overview).

### Downloading FastApp Studio

Once you have installed the platform, you must download Profisee FastApp Studio to perform the following steps. Profisee FastApp studio is the main administration application used to configure various aspects of the Profisee Platform. To access the software for Profisee FastApp studio, navigate to *https://<ServerName>/<ProfiseeVirtualDirectory>/api/client/*in your browser's URL bar and select the desired FastApp Studio download.

Once you have obtained your Profisee Credentials and installed the requisite software, you are ready to [log into](https://support.profisee.com/wikis/profiseeplatform/log_in_to_the_profisee_platform) the Profisee platform using your previously-obtained credentials and begin creating a data model.

Creating a Model

Now that the Profisee Platform is installed, you must import metadata to be managed by the Profisee Platform. Though it is possible to [create a new data model](https://support.profisee.com/wikis/profiseeplatform/create_a_new_model) from scratch, it is much more likely that you will import an established data model already used by your organization.

To do so, navigate to the **Advanced Modeling** tab on the left-hand side of the application. From here, you have three ways to import a data model.

- [Open a model from a file](https://support.profisee.com/wikis/profiseeplatform/open_a_model_from_a_file) (if a Profisee model file exists on your machine)
- [Import a model from SQL Server](https://support.profisee.com/wikis/profiseeplatform/import_from_sql_server)

Once you have imported the model you wish to use in your data structure, you can click [Save](https://support.profisee.com/wikis/profiseeplatform/save_a_model_as_a_file) on the topmost toolbar to locally save the model as a file on your machine. Once you are ready to begin working with the model, click **Publish to Server** to publish the metadata changes to Profisee Platform. You must publish all changes before continuing to work with the model in Profisee FastApp Studio.

Using **[Adaptive Modeling](https://support.profisee.com/wikis/profiseeplatform/adaptive_modeling_overview)**, you can manually create, edit, and remove entities from your model immediately. You can access this feature by clicking the **My Workspace** tab in FastApp studio, then selecting **New Workspace**, then selecting **Entity**. Adaptive Modeling is a helpful tool for creating specific entities in limited numbers.

## Adding Data into FastApp Studio

Once you have an established model, you can add, edit, and remove metadata from your Profisee instance. The most common way to do this is by managing entities.

You can add [records to an entity grid](https://support.profisee.com/wikis/profiseeplatform/add_a_new_member_in_the_entity_grid) to manually add values to an entity grid. You can also [Import Data from Excel](https://support.profisee.com/wikis/profiseeplatform/create_a_new_model) to use data from a Micro Excel File to create records within an entity grid.

To add data to your model en masse, you can navigate to the [**Staging Tables**](https://support.profisee.com/wikis/profiseeplatform/staging_tables_overview) tab on the left-hand toolbar of the application to import bulk loads of data into your model at once.

Once you are satisfied with the data included in your Profisee instance, you should create a FastApp to allow other users to view and manage the data in a user-friendly manner.

## Creating your first FastApp

Once your data model is in place and filled with all necessary entities, you can create a FastApp Portal Application that allows other users to access the data they will work with most frequently to meet specific business or organizational needs.

To [create a new FastApp](https://support.profisee.com/wikis/profiseeplatform/create_a_new_fastapp), an administrator must perform the following steps:

1. [Configure the Application Context Dialog](https://support.profisee.com/wikis/profiseeplatform/configure_the_application_context_dialog)
2. [Add a New Application Page](https://support.profisee.com/wikis/profiseeplatform/add_a_new_portal_application_page)
3. [Add an Entity Grid Control](https://support.profisee.com/wikis/profiseeplatform/configure_the_entity_grid_control)
4. [Link Controls](https://support.profisee.com/wikis/profiseeplatform/link_controls) (where applicable)
5. [Configure Settings on the Menu Tab](https://support.profisee.com/wikis/profiseeplatform/configure_app_admin_menu_tab)

Depending on the controls used and preferences for the way data displays, you may also need to complete the following before creating the new application:

- [Create a New Form](https://support.profisee.com/wikis/profiseeplatform/create_a_new_form)
- [Create a New Presentation View](https://support.profisee.com/wikis/profiseeplatform/create_a_new_presentation_view)

Once you have created your FastApp Portal application, you can launch the portal by entering *http://[serverName]/Profisee* into the URL bar of your browser.

As of version 2021.R2, Internet Explorer is not a compatible web browser for navigating FastApp Portal applications.

From here, you can [navigate the Profisee FastApp Portal](https://support.profisee.com/wikis/profiseeplatform/portal_overview) to work within the previously configured forms, entity grids, tasks, and hierarchies previously established during the portal configuration process.

## What's Next?

Congratulations! You have successfully created a functioning instance of the Profisee Platform. However, the Profisee Platform provides a vast array of functionalities that can greatly improve your data management experience and efficiency with the product. Many of these functionalities are simple, while others require more detailed learning and experience.

The following is a list of recommended tools to experiment with to improve the quality of your Profisee instance.

- [Data Quality Rules](https://support.profisee.com/wikis/profiseeplatform/data_quality_rules_overview)
- [Matching and Survivorship](https://support.profisee.com/wikis/profiseeplatform/matching_and_survivorship_overview)
- [Workflows](https://support.profisee.com/wikis/profiseeplatform/what_are_workflows)