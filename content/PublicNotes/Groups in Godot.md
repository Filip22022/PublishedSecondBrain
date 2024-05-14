---
title: Groups in Godot
Date created: 2024-05-09 10:40
Aliases:
tags: 
  - Public
---

Groups are a tool that allows you to assign 'tags' to scenes sharing a similar behaviour or needing to be accessed together in [[Godot]] 
## Managing Groups
Adding and removing nodes form a group can be done in two ways:
- Through the Node -> Groups tab in the editor
- With `add_to_group()` and `remove_from_group()`

## Working with the Groups
Groups are useful because they provide two key functionalities:
- The ability to get all members of the group from the whole `SceneTree` 
	`get_tree().get_nodes_in_group("<group>")`
- The ability to call a function of every member of the group.
	`get_tree().call_group("<group>", "function_name"`