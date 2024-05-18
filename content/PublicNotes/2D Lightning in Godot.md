---
title: 2D Lightning in Godot
Date created: 2024-05-14 10:30
Aliases:
tags: 
  - Public
---

Godot offers the ability to use real-time light and shadows for 2D projects to enhance the default unshaded bland scenes.

## Light Related Nodes
- `Canvas Modulate` - to darken the scene outside of light
- `PointLight2D` - Torch light, projectile light, etc
- `DirectionalLight2D` - Sunlight/Moonlight
- `LightOccluder2D` - Shadow casters
### Setup Point Light Texture in Godot Editor
To create a circular gradient light texture select `new GradiadientTexture2D ` and edit the textures `Fill -> Fill` property to `Radial`. Then you can edit the texture and it's gradient to achieve desired result.

## Setting up Shadows
To create shadows in the scene, change light node `Shadow` property to `Enabled` and add `LightOccluder2D` nodes to objects that should cast shadows. Those nodes must also have occluder polygons.

### Prevent Certain Objects from Casting Shadows
Using the light node's `Item Cull Mask` and the occluder's  `Occluder Light Mask` it is possible to prevent specific objects from receiving light from specific sources

### Generating a Light Occluder
On a `Sprite2D` node, you can choose Sprite2D menu at the top of the editor -> `Create LightOccluder2D Sibling` to generate occluder automatically. 
Adjust the occluder by using `Grow(pixels)` and `Shrink(pixels)` -> `UpdatePreview` and confirm with `OK` to finalize the occluder

### Drawing a Light Occluder

Important properties:
- Filter - Default lack of filter is the fastest and blocky, PCF5 is a softer shadow, and PCF13 is even softer, but very demanding to render
- Filter Smooth - how much softening is applied with PCF5/13

### Shading the Sprite Itself
Due to the drawing order, if the occluder is a _sibling_ of the sprite, it will shade the sprite if it's placed below it.
If the occluder is the _child_ of the sprite, it will shadow the sprite if `Show Behind Parent` is disabled (default)

## Improving Depth with Normal and Specular Maps
Normal and Specular maps can reduce the perceived flatness by varying light intensity depending on the light receiving surface's direction.

Normal map defines directions in which pixels are pointing which allows the engine to apply lightning better, while a specular map defines how much each pixel reflects light and in what color.

Free and open source tool for generating maps for sprites: https://azagaya.itch.io/laigter

### Setting up Maps on a 2D Node
To set up a normal and/or specular map create a new `CanvasTexture` resource for the node's texture.