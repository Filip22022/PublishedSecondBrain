---
title: Animating Sprites in Godot
tags: 
  - Public
Aliases:
Date created: 2024-03-21 19:37
---

[Documentation](https://docs.godotengine.org/en/stable/tutorials/2d/2d_sprite_animation.html)

Animating 2D sprites in Godot cna be done in two main ways:
- Using `Sprite` and `AnimationPlayer` nodes and a spritesheet
- Using `AnimatedSprite` node and individual frame sprites 


### Collision Shapes

>[!Warning]
>While `AnimationPlayer` can make the collision shape follow the sprite, I don't know if it's possible to achieve similar effect using `AnimatedSprite`. 
>A possible workaround is to create a bigger shape encompassing full range of motion or few individual hitboxes that are cycled through on `frame_changed` signal.


To animate the collision shape together with the sprite, the position of the `CollisionShape` has to be tracked (Node2D -> Transform -> key icon on the right)

example: [Animation layer and collision combat](https://www.youtube.com/watch?v=8EVHNbgQCBg&ab_channel=LearnICTNow)