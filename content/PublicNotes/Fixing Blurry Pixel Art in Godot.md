---
title: Fixing Blurry Pixel Art in Godot
Date created: 2024-05-09 11:26
Aliases:
tags: 
  - Public
---

When importing pixel art in Godot, the sprites can appear blurry due to default filtering mode set on the `Sprite` node

## Fix for a Single Sprite
In the  `Inspector` tab under `CanvasItem` -> `Texture` -> `Filter` set it to `Nearest` to get the clear image.

## Fix for a Project
To change the default filtering for the whole project access `Project Settings` -> `Rendering` -> `Textures` -> `Default Texture Filter` and change from `linear` to `nearest`