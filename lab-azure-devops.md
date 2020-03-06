---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Lab - Azure DevOps
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
    prev:
        content: Intro to Kubernetes
        url: '/lab-kubernetes'
    next: 
        content: Whiteboard Sessions
        url: '/lab-whiteboards'
---

## The Lab

<div class="callout callout--warning">
    <p><strong>Wait a sec</strong> Did you do the pre-requisites?
    You'll need an Azure DevOps organization and a sample project as created by the demo generator. </p>
</div>

<div class="callout callout--danger">
    <p><strong>Feature Flag</strong> If you don't see a <b>pipelines</b> menu item, you have to <b>enable multi-stage builds</b>
    
    <br />
    <img src="/images/preview-feature-pipelines.jpg" />

    <br />
    If you need help enabling this feature, <a href="https://docs.microsoft.com/en-us/azure/devops/project/navigation/preview-features?view=azure-devops#enable-features-for-your-use">see here</a>
    </p>
</div>

## Create a new CI/CD pipeline

The pipelines in our project use the classic approach, that is, they are managed exclusively on the portal via a point and click interface. Microsoft also supports creating and managing these pipelines in YAML (Yet Another Markup Language). Doing so allows for local editing of pipelines as well as auditing and history via source control systems. This is the standard moving forward, part of Pipelines as Code PaC).

Let's create a new pipeline using YAML to build our **PartsUnlimited** web application.

### Part 1: Create the YAML Template
We can create new Pipelines by accessing the Pipelines section of our project ![](/images/pipelines.png)

There you will find the **New pipeline** button in the upper right hand corner. After clicking it following these steps:

1. For the **Where is your code?** question, select **Azure Repos Git**
2. Only one project should exist called **PartsUnlimited** - select it
3. Select **Starter pipeline** - this will produce a mostly empty pipeline
4. Delete all contents on **Line 13** to the end from the starter template

We are now ready to add tasks to perform operations on our code.

### Part 2: Update the YAML Template with the appropriate tasks
Be sure your cursor is positioned on **Line 13** and click **Show assistent** on the right hand side just beneath the **Save and Run** button. Doing so will the list of tasks that can be added to the build script

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

Press the **Save and Run** button. A dialog will appear to allow for a custom commit message to describe what is being done. For now, just take the default. Click **Save and Run** once more. This will queue the build action.

To see the status of the build click **Pipelines** near the top of the screen. You should see your building running at the top. Clicking on it will allow you to drill into it.

Congratulations!! 

You have just set up your first YAML pipeline.
