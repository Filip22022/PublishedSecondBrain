---
title: Angular Naming Convention
Date created: 2024-04-16 17:31
Aliases:
tags: 
  - Public
---

The [Angular Style Guide](https://angular.io/guide/styleguide) contains rules and suggestions about naming when working with Angular

## Naming Rules

### Be Consistent
Consistency is the most important factor to keep the codebase clear and readable, especially if cooperating on a larger project.

The recommended pattern is
`descriptive-name.type.ts`

### Use Dashes and Dots
Use dashed to separate words in a longer descriptive name
Use dots to separate descriptive name from the type 

### Use Conventional Type Names
Limit inventing additional type names for simplicity
conventional names include: `.service`, `.component`, `.module`

### Class Naming
Name the classes using upper camel case, and append it with the type suffix
example: `class MyAppComponent`

### Match Symbol name to Filename
`class MyAppComponent` should be placed in file `my-app.component.ts`

### Service Naming
Services should be named after their feature with `-Service` suffix, or be clearly service names, such as `Logger`

### Component Selector Naming
#### Component Selector
Selectors should use *dashed-case* or *kebab-case*

#### Use a Component Prefix
To avoid name collisions use a custom prefix for a component selector, use lowercase hyphenated prefix
example: `selector: 'admin-users'`

### Directive Selector Naming
Use *lower camel case* for directive selectors and use custom prefix

### Test File Naming

#### Unit Test Files
Name test specification files the same as the tested component with `.spec` suffix
#### End-to-End Test Files
Name End-to-End test specification files after the tested feature with `.e2e-spec` suffix

