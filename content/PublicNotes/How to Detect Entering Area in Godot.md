---
title: How to Detect Entering Area in Godot
Date created: 2024-04-26 12:42
Aliases:
tags: 
  - Public
---

In [[Godot]] Area2D has two signals that are emitted when something enters it's collision shape.
- `body_entered` emitted when `PhysicsBody2D` enters the area
- `area_entered` emitted when `Area2D` enters the area

The *detecting* area needs to mask the layer, that the *detected* are is on.  