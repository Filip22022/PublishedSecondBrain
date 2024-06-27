---
title: Data Transfer Object
Date created: 2024-06-20 11:30
Aliases: DTO
tags: 
  - Public
---

A Data Transfer Object are objects designed to carry data between processes to reduce the number of method calls necessary.

They are flat data structures, containing no business logic, but possibly having storage, accessors, and methods related to serialization and parsing.

The DTO's can have properties from several classes, or conversely only a part of properties of a class.


### Mapper
To transfer the data between a DTO and a model, we create a *mapper* component to decouple the different layers.

### Common Mistakes
We should avoid creating too many DTO's to not increase the number of classes and mappers to maintain. On the opposite extreme we should also avoid creating bloated DTO's that fit many scenarios.