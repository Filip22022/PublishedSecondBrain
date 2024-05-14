---
title: Renaming nodes in Godot
Date created: 2024-05-04 12:53
Aliases:
tags: 
  - Public
---

In Godot a node's name has to be unique among its siblings. When a node is named automatically when using `add_child` it will be named after its type with a number suffix if needed.

To rename a node, change it's `name` property by using `set_name(StringName)` method.