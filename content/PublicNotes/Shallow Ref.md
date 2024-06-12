---
title: Shallow Ref
Date created: 2024-06-11 12:54
Aliases:
tags: 
  - Public
---

Shallow version of a [[Ref Object]] in which the value is not deeply reactive. The values is stored and exposed as-is and only `.value` access is reactive.

Typically used for performance optimizations when observing a large data-structure is costly
