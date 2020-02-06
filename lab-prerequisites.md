---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Lab - Get things setup
description: Ignore the bad name. Let's adopt some DevOps practices using Azure DevOps.

# Author box
author:
    title: About Author
    title_url: '#'
    external_url: true
    description: Facundo is a Cloud Solutions Architect at New Signature. He enjoys helping clients with architecture, containers/orchestration, and stream lining development processes.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    next: 
        content: Lab - Docker
        url: '/lab-docker'
---

## Create an Azure DevOps Account
An Azure DevOps account will give you access to Microsoft's full featured platform for managing code, tasks, and automation. We will use these features in future labs

If you don't have an Azure DevOps account, follow these steps to create a new **Azure DevOps Organization**. (They are _not_ called accounts because multiple team members can be part of one)

1. Go to <a href="http://dev.azure.com" target="_blank">https://dev.azure.com</a>
2. Click on "Start Free"
3. Sign In using either:
    - Your Organization's Azure AD account
    - Your Personal Microsoft Account (Feel free to create one if you need to)
4. Get Started with Azure DevOps
![](/images/get-started-azure-devops-2.jpg)
5. Create a simple starter project (this will be empty) with the following information:
    - **Project name:** - My First Project
    - **Description:** - *(empty)*
    - **Visibility:** - Private

Upon hitting **Create Project** Azure DevOps will create a new project for you.
Congratuations!! You have just created your first Azure DevOps project, now lets explore all the platform has to offer.

## Getting Familiar with your Project
Azure DevOps provides a wealth of management features, all available along the left hand side navigation. Let's briefly explore each of these
<img src="images/left_navigation.png" />
- **Overview** - This is the default landing page and supports a variety of dashboards for tracking progress. You can also add files to describe the project including Wiki pages for team knowledge sharing

- **Boards** - This is where you will manage User Stories, Tasks, Bugs, etc. It is a complete planning and tracking platform for your project(s) capable of supporting Scrum, Agile, Kanban, and other methodologies

- **Repos** - This is where the code for your projects are stored. By default an Azure DevOps project will have a single code repository but, teams can create as many repositores as needed for how they want to organize the code for their project

- **Pipelines** - This is where any automated build and deployment pipelines are executed and observed. These pipelines serve a valuable role of bringing consistent and efficient process to teams to enable developer to focus higher value items

- **Test Plans** - This is a full suite of tools for creating, managing, and executing test plans using both code and recorded point and click steps. Provides numerous visualizations pertaining to quality and performance

- **Artifacts** - This is a fully managed storage area for project related artifacts including Test Plan Results, Code Metrics storage, library caching, and custom library hosting.

All of these pieces together enable Azure DevOps to provide a complete end to end solution for your project all in once place.

Now that we have a feel for the portal, let's generate a new sample project with  the **Azure DevOps Demo Generator**.

## Create Sample Project

For the Sample Project, we can use the afore mentioned Demo Generator. Microsoft has laid out how to do this so, for now, hope over to [these instructions](https://www.azuredevopslabs.com/labs/azuredevops/prereq/) to create a Team Project. **Only complete Task 1**

At the end please make sure you **Navigate to project** - this will take you to the newly created project in Azure DevOps, the screen will be similar to what you saw when you crated the Test Project previously.

### Exploring Parts Unlimited
The generator application has created many artifacts within the project, let's take a moment to explore some of the more important ones:

- Under **Repos** you will see a repository was created called **PartsUnlimited** with all of the code for our application. For those interested, this is a Git repository and it can be cloned locally.

- Under **Pipelines** the template has created pipelines under the **Pipelines** and **Releases** subsections. These are automation artifacts that enable code to be built automatically with each checkin (Continuous Integration) and then deployed once that build completes (Continuous Deployment).
    - In the default state after generation, the Release pipeline will contain placeholders that can be updated later to deploy the application to Microsoft's public cloud - Azure.

## Stretch Goal: Create a new build pipeline using YAML
Currently our project leverages the classic approach to build and manage pipelines by creating them through the point and click interface. While this works for some cases progressively, we are seeing the desire to enable proper versioning and auditing of these pipelines. To address this, Microsoft enables build and release pipelines to be built using YAML (Yet Another Markup Language).

Pipelines built in YAML are text files that we can add to our source control repository and version over time with full history. Collectively, this is know as Pipeline as Code (PaC) in the industry.

### Part 1: Create the YAML Template
We can create new Pipelines by accessing the Pipelines section of our project <img src="images/pipelines.png" />

There you will find the **New pipeline** button in the upper right hand corner. After clicking it following these steps:

1. For the **Where is your code?** question, select **Azure Repos Git**
2. Only one project should exist for **PartsUnlimited** - select it
3. Select **Starter pipeline** - this will produce a mostly empty pipeline
4. On the next screen you will be shown the default starter template. Delete all contents on **Line 13** to the end

We are now ready to add tasks to perform operations on our code.

### Part 2: Update the YAML Template with the appropriate tasks
Be sure your cursor is positioned on **Line 13** and click **Show assistent** on the right hand side just beneath the **Save and Run** button. Doing so will show you a list of tasks you can add to your template.

1. On **Line 10** update the **vmImage** to be **vs2017-win2016**
2. Type '*visual*' in the *Search tasks* text field. Select **Visual Studio build**
3. For **Platform** and **Configuration** input the following
    - **Visual Studio Version** - 2017
    - **MSBuild args**
    ```
    /p:DeployOnBuild=true /p:WebPublishMethod=Package /p:PackageAsSingleFile=true /p:SkipInvalidConfigurations=true /p:PackageLocation="$(build.stagingDirectory)" /p:IncludeServerNameInBuildInfo=True /p:GenerateBuildInfoConfigFile=true /p:ReferencePath="C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Extensions\Microsoft\Pex"
    ```
    - **Platform** - any cpu
    - **Configuration** - release
    - **Advanced::Restore NuGet Packages** - checked

4. Ensure **clean** is checked
5. Press the **Add** button at the bottom. This will add the appropriate YAML to your file at the location of the cursor

Now that our application is being builtour work is mostly complete. Next, we will *publish* the generated artifact from the Visual Studio build task so that our generated artifact is available for use in Release pipelines.

1. Ensure your cursor is placed on a new line directly inline with the '-' for the previous task.
2. Type '*publish*' in the *Search tasks* text entry field. Select **Publish build artifacts**
3. Change the **Path to publish** to *$(Build.StagingDirectory)*. Leave everything else as is
4. Click the **Add** button to add the correct YAML to your script

### Part 3: Test Your Script
Now that we have a complete YAML script for building our application we can save the file. By default, it will be saved as **azure-pipelines.yml** at the root our repository.

Press the **Save and run** button. A dialog will appear to allow for a custom commit message to describe what is being done. For now, just take the default. Click **Save and run** once more. This will queue the build action.

To see the status of the build click **Pipelines** near the top of the screen. You should see your building running at the top. Clicking on it will allow you to drill into it.

Congratulations!! You have just set up your first YAML pipeline.