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

## Pre-Requisites

Before you get started, you'll need to create an Azure DevOps organization

### Create an Azure DevOps Account

If you don't have an Azure DevOps account, follow these steps to create a new **Azure DevOps Organization**. (They are _not_ called accounts because multiple team members can be part of one)

1. Go to <a href="http://dev.azure.com" target="_blank">https://dev.azure.com</a>
2. Click on "Start Free"
3. Sign In using either:
    - Your Organization's Azure AD account
    - Your Personal Microsoft Account (Feel free to create one if you need to)
4. Get Started with Azure DevOps
![](/images/get-started-azure-devops-2.jpg)

That's it! **You don't have to create a new project.**

### Create a Sample project

Next, let's use the Azure DevOps Demo Generator to import a sample project.
Follow the instructions [on this page](https://www.azuredevopslabs.com/labs/azuredevops/prereq/) to create a Team Project. **Only complete Task 1**

Once you're done, come back here to continue the lab.

## The Lab

<div class="callout callout--warning">
    <p><strong>Wait a sec</strong> Did you do the pre-requisites?
    You'll need an Azure DevOps organization and a sample project as created by the demo generator. </p>
</div>

<div class="callout callout--danger">
    <p><strong>Feature Flag</strong> If you don't see a <b>pipelines</b> menu item, you have to <b>enable multi-stage builds</b>
    <img src="/images/preview-feature-pipelines.jpg" />

    If you need help enabling this feature, <a href="https://docs.microsoft.com/en-us/azure/devops/project/navigation/preview-features?view=azure-devops#enable-features-for-your-use">see here</a>
    </p>
</div>

Now, you're ready to [follow this lab](https://www.azuredevopslabs.com/labs/azuredevops/continuousintegration/) for implementing Continuous Integration on your new team project.

## Stretch Goal

### Create a CI/CD Pipeline using YAML

Now, instead of clicking around like a crazy person, using YAML to create your pipelines.
