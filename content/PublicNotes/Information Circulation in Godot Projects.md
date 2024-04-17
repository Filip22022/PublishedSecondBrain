---
title: Information Circulation in Godot Projects
Tags: Public
Aliases:
Date created: 2024-03-25 13:14
---

# Information Circulation in Project


[This discussion](https://www.reddit.com/r/godot/comments/10cbpyj/get_parent_and_get_node_considered_harmful/) touches on the best practices of accessing the parent object from the child objects and also objects in the tree that are not children.

While the counterarguments to the main post argument well, that in some cases those behaviours have their place, the original post also has a point in structuring code in a cleaner way.

## Signals Vs Calls
### General Rules

Two rule of thumbs takeaways:
- Function calls go downstream (towards descendants)
- Signal emissions go upstream (towards ancestors/roots) 

### Signalling to Siblings
To avoid having to call a sibling by it's path to connect the signal, the connection should be made by the common parent of the sibling nodes.


## Using Groups
Groups in godot are a tagging system

Nodes can be added to groups, which can then be managed as a whole. This is useful decoupling mechanism for different nodes that should behave identically under some circumstances.

To add node to group you can use the 'Node>Groups' tab in the editor or use `add_to_group(name: String)` function from code. Similarly `remove_from_group(name: String)` will remove the node it's called on from the group `name` 

To invoke an action on all members of a group we can use the following code:
```gdscript
func foo():
	get_tree().call_group("x", "do_y")
```

## `Owner` Property
The `owner` is a node property pointing to the scene's root node. It can be conveniently used to connect child signals to the main node.

### Example
When having multiple buttons in a scene we can use the owner property to quickly connect them to the root script

```gdscript
func _ready():
	presssed.connect(owner._on_button_pressed)
```