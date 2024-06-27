---
title: Vue Naming Guide
Date created: 2024-06-16 09:42
Aliases:
tags: 
  - Public
---

### Components
- Should be multi-word
- Should use `PascalCase` or in [[Single-File Components|SFC's]] and `kebab-case` for in-DOM templates 
- Components that are tightly coupled with their parent should include parent name as prefix
- Order words from highest-level to descriptive modifying words
- Component names should use full words over abbreviations


### Props
- Should use `camelCase` for declaration and usage in SFC's, for usage in in-DOM templates use `kebab-case`