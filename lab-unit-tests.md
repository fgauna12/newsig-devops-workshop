---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Lab - Unit Tests
description: Now for the best part - adding unit tests!

# Author box
author:
    title: About Author
    title_url: '#'
    external_url: true
    description: Facundo is a Cloud Solutions Architect at Nebbia Technology. He enjoys helping clients with architecture, containers/orchestration, and stream lining development processes.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Characterization Tests
        url: '/lab-characterization'
---

## Overview

Now that the source code is cleaner, start adding some unit tests. **Run your characterization and newly created unit tests often.**

### Useful Packages

- [Moq](https://github.com/moq/moq)
- [Fluent Assertions](https://fluentassertions.com/)
- [Bogus](https://github.com/bchavez/Bogus)

## Make some unit tests!

### Start with `ProductsController.Get`

Know that you know some of the characteristics of the code and how it behaves *and* you have refactored it using well-known practices. Add some unit tests for the test cases you do know. **It's ok to keep refactoring**, it didn't have to be perfect the first time.

Run your tests often.

### Stretch Goal

- Refactor your unit tests simple to read
