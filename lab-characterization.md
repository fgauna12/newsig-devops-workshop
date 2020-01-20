---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Lab - Characterization Tests
description: Daunted by unfamiliar legacy code? Let's practice

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
        content: Getting Started
        url: '/getting-started'
    next:
        content: Unit Tests
        url: '/lab-unit-tests'
---

## Overview

You've been tasked with creating a new feature. Clearly, the code is not in the best shape. So you decide you want to do some refactoring and add automated tests. Nice! the boyscout rule - leaving things better than you found them.

Before we start creating the feature, let's create some **characterization tests**. Characterization tests help us learn from the system and how it's currently in production. This is extremely useful when learning what a system does and how it works. If you'd like a refresher on characterization tests, there's a really good [blog post](https://michaelfeathers.silvrback.com/characterization-testing) from Michael Feathers.

### Useful Links

- [Testing Controller Logic in ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/mvc/controllers/testing?view=aspnetcore-2.2)
- [Parsing Results from ActionResult](https://stackoverflow.com/a/51489502)

## Write Characterization Tests

Become familiar with the code. Don't refactor. Let's start with a single method and be inquisitive. 

### Start with `ProductsController.Get` 

Feel free to create a test project. Start experimenting and creating a characterization test to understand how it works today.

As you start learning, create some test cases to start documenting given some criteria what the expected results are.

<div class="callout callout--warning">
    <p><strong>Note:</strong> If you are new to ASP.NET Core, when you create a test project, make sure it is in <em>.NET Core</em> and it uses <b>Microsoft.AspNetCore.App</b> NuGet package
    </p>
</div>

<div class="callout callout--danger">
    <p><strong>Note:</strong> Remember, don't start refactoring right away. You have running database using docker. Feel free to connect to it using your tests and expirement away.
    </p>
</div>


#### How do I know I'm done?

- Do you have a good idea about the kind of refactorings you'd to do to start breaking dependencies?
- What would it take to start making this code more unit testable?
- Do you comfortable enough to start refactoring without breaking it?

## Refactor

Create an end-state in mind of what you would like the architecture to look like. For example, what would the code look like if it was using:

 - Dependency Injection 
 - SOLID Principles 
 - Clean Architecture

<div class="callout callout--success">
    <p><strong>Don't Forget:</strong> Run your characterization tests often to make sure your refactoring is not breaking things.</p>
</div>

Checkout the [Resources](/resources) tab for useful links.

## Stretch Goal 

 - What happens when the database goes down? Can you similate this?
 - Write some characterization tests for `ProductsController.Consume`
 - Refactor with what you're comfortable




