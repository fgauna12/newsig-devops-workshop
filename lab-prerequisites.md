---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Lab - Get things setup
description: Don't have an Azure DevOps Account? No problem.

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

Hit **Create Project**. Azure DevOps will create this new project for you. Once complete let's look over what the platform offers before we move on to additional tasks.

## Getting Familiar with the DevOps Portal
Azure DevOps provides many features for managing the development of an application. Each of these features are made available in the left hand navigation bar, shown below/

![](/images/left_navigation.png)

- **Overview** - This is the default landing page and supports a variety of dashboards for tracking progress. You can also add files to describe the project including Wiki pages for team knowledge sharing

- **Boards** - This is where you will manage User Stories, Tasks, Bugs, etc. It is a complete planning and tracking platform for your project(s) capable of supporting Scrum, Agile, Kanban, and other methodologies

- **Repos** - This is where the code for your projects are stored. By default an Azure DevOps project will have a single code repository but, teams can create as many repositores as needed for how they want to organize the code for their project

- **Pipelines** - This is where any automated build and deployment pipelines are executed and observed. These pipelines serve a valuable role of bringing consistent and efficient process to teams to enable developer to focus higher value items

- **Test Plans** - This is a full suite of tools for creating, managing, and executing test plans using both code and recorded point and click steps. Provides numerous visualizations pertaining to quality and performance

- **Artifacts** - This is a fully managed storage area for project related artifacts including Test Plan Results, Code Metrics storage, library caching, and custom library hosting.

While all are useful to a degree, the one's we will focus on for the rest of this lab will be **Repos** and **Pipelines**.

Now that we have a feel for the portal, let's generate a new sample project with  the **Azure DevOps Demo Generator**.

## Create Sample Project

For the Sample Project, we can use the afore mentioned Demo Generator. Microsoft has laid out how to use tool to create a project we can use in our Azure DevOps account. Use [these instructions](https://www.azuredevopslabs.com/labs/azuredevops/prereq/){:target="_blank"} to create the project we will use for the rest of this lab. **Only complete Task 1**

Upon project import completion make sure you **Navigate to project** - this will take you to the newly created project in Azure DevOps, the screen will be similar to what you saw when you created the Project in the previous section.

### Exploring Parts Unlimited
The imported application will have created artifacts to support our new application, some of the more important ones are:

- **Repos** will now contain the code for our application (**PartsUnlimited**). For those interested, this is a Git repository and it can be cloned locally.

- **Pipelines** will not contain classic style pipelines for Build (under the **Pipelines** subsection) and Reease. These artifacts enable code to be built automatically with each change (Continuous Integration) and automatically deployed thereafter (Continuous Deployment).
