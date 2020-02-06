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
    <img src="/images/preview-feature-pipelines.jpg" />

    If you need help enabling this feature, <a href="https://docs.microsoft.com/en-us/azure/devops/project/navigation/preview-features?view=azure-devops#enable-features-for-your-use">see here</a>
    </p>
</div>

Now, you're ready to [follow this lab](https://www.azuredevopslabs.com/labs/azuredevops/continuousintegration/) for implementing Continuous Integration on your new team project.

## Stretch Goal

### Create a CI/CD Pipeline using YAML

Now, instead of clicking around like a crazy person, using YAML to create your pipelines.
